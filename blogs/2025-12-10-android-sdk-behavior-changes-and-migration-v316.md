---
title: "Android SDK Behavior Changes and Migration (v3.16+)"
url: "https://developer.webex.com/blog/android-sdk-behavior-changes-and-migration-v3-16"
date: "Wed, 10 Dec 2025 00:00:00 GMT"
author: "Rankush Kumar"
feed_url: "https://developer.webex.com/blog/feed"
---
<img alt="Android SDK Behavior Changes and Migration (v3.16+)" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blte4ed20cb4826bd3a/693994413a0ed89e77a7b62e/mobile_sdk_blog.png?width=900&amp;height=317&amp;fit=crop" /> <p>We're excited to announce the release of Mobile SDK version 3.16.0v, bringing with it important updates and enhancements for your Android applications. This release focuses on improving compatibility, flexibility, and compliance with the latest Android platform guidelines. While some changes are seamless, others require your attention for a smooth migration.</p>
<p>This guide will walk you through two significant behavior updates introduced in the <a>Android SDK</a> (now available on the <a href="https://github.com/webex/webex-android-sdk" rel="noopener noreferrer" target="_blank">GitHub repo</a>) and provide clear instructions on how to migrate your apps:</p>
<ul>
<li><strong>Support for 16 KB memory page size</strong> (Google-recommended platform change)</li>
<li><strong>App-owned runtime permission handling</strong> (SDK no longer prompts)</li>
</ul>
<p>Both of these are intentional behavior changes. The 16 KB memory page size work is designed to be non-breaking for existing applications, requiring minimal effort on your part. However, the new permission model is a breaking change that necessitates specific updates to your app's code and manifest to ensure continued functionality. Let's dive into the details of each.</p>
<h6>1. 16 KB memory page size (what, why, and what changed)</h6><br />

<h6>What is the 16 KB page-size recommendation?</h6><p>Newer Android devices and toolchains are increasingly adopting a default memory page size of 16 KB on arm64 architectures. Google has made this a crucial Play Store compatibility requirement: starting November 1, 2025, all new apps and updates targeting Android 15+ devices must fully support 16 KB page sizes on 64-bit devices. For more detailed guidance, refer to Google's official documentation: <a href="https://developer.android.com/guide/practices/page-sizes" rel="noopener noreferrer" target="_blank">Google: Support 16 KB page sizes</a>.</p>
<h6>What we changed in the SDK</h6><p>To ensure your applications remain compliant and perform optimally, we've made the following adjustments within the Webex Mobile SDK:</p>
<ul>
<li>We've updated native components and packaging to be fully compatible with 16 KB memory pages, including proper ELF alignment, toolchain flags, and mapping behavior.</li>
<li>We've thoroughly ensured that the SDK runs correctly on devices utilizing 16 KB pages without requiring any app-side code changes from you.</li>
</ul>
<br />

<h6>Migration impact for apps</h6><p>The good news here is that no app code changes are required for this particular update. Simply updating to this latest SDK version is sufficient to gain 16 KB page size compatibility.</p>
<ul>
<li><strong>Validation tip:</strong> To verify this on a test device or emulator, you can use <code>adb shell getconf PAGE_SIZE</code>. It should return <code>16384</code> when running with 16 KB pages (as described in the Google doc linked above).</li>
</ul>
<br />

<h6>2. App-owned permission flow (breaking change)</h6><p>This is a significant update that provides greater control and flexibility to app developers. Previously, the SDK handled certain aspects of permission management, but with 3.16.0v, this responsibility shifts entirely to the application.</p>
<h6>What changed</h6><ul>
<li><strong>Manifest Declarations:</strong> The SDK no longer includes dangerous permissions in its library manifest. Applications must now explicitly declare all necessary permissions in their own <code>AndroidManifest.xml</code>.</li>
<li><strong>Runtime Requests:</strong> The SDK will no longer prompt users for system permissions. It is now the application's responsibility to request these permissions at runtime.</li>
<li><strong>Preflight Checks:</strong> The SDK will perform preflight checks. If required permissions are missing, it will report this via <code>WebexError.ErrorCode.PERMISSION_REQUIRED</code>, providing a list of the missing permissions in <code>error.data</code>.</li>
<li><strong>Screen Sharing Consent:</strong> There is also a change in how user consent for screen sharing is obtained, moving towards an app-driven approach.</li>
</ul>
<br />

<h6>Why we changed it</h6><p>This shift to app-owned permission handling offers several key advantages for developers:</p>
<ul>
<li><strong>Flexibility:</strong> It allows apps to adopt the latest Android UX patterns for permission prompts, enabling custom UI flows that integrate seamlessly with your app's design.</li>
<li><strong>Independence:</strong> This change reduces app coupling to SDK releases, making your application less susceptible to changes when Google updates its permission policies.</li>
<li><strong>Store Compliance:</strong> Apps gain better control over which permissions are declared per build flavor, helping to minimize Play Console warnings related to dangerous or sensitive permissions.</li>
</ul>
<br />

<h6>Why it’s a breaking change</h6><p>This update is classified as a breaking change because:</p>
<ul>
<li>Apps that previously relied on the SDK to display permission dialogs will now receive <code>PERMISSION_REQUIRED</code> errors instead of the expected pop-ups.</li>
<li>Migration is required. You will need to add explicit manifest declarations, implement runtime permission requests, and include logic to retry SDK calls after permissions have been granted by the user.</li>
</ul>
<br />

<h6>Migration Guide (step by step)</h6><p>To help you seamlessly transition to the new permission model, follow these step-by-step instructions.</p>
<h6>A. Manifest preparation (app-side)</h6><p>It's crucial to declare only the permissions your app truly needs for its specific features or build flavors. This minimizes unnecessary permission requests and improves user trust. Here are some common examples:</p>
<ul>
<li><code>RECORD_AUDIO</code> (for audio functionality)</li>
<li><code>CAMERA</code> (for video functionality)</li>
<li><code>MODIFY_AUDIO_SETTINGS</code> (required for audio routing, such as switching between speaker, Bluetooth, or earpiece)</li>
<li><code>BLUETOOTH_CONNECT</code> on API 31+ (for Bluetooth route toggling; use legacy <code>BLUETOOTH</code> for older Android versions)</li>
<li><code>READ_PHONE_STATE</code> (an optional optimization, as detailed below)</li>
<li>Note that there is no runtime string for screen share consent (MediaProjection). If your user experience requires overlays (e.g., for annotations), <code>SYSTEM_ALERT_WINDOW</code> will be needed.</li>
</ul>
<br />

<h6>B. Common runtime request utility</h6><p>We recommend creating a small helper utility to check for and request permissions before invoking SDK APIs. This promotes cleaner code and consistent handling.</p>
<pre><code class="language-kotlin">val required = listOf(Manifest.permission.RECORD_AUDIO)
val missing = required.filter { ContextCompat.checkSelfPermission(ctx, it) != PackageManager.PERMISSION_GRANTED }
if (missing.isNotEmpty()) {
    // requestPermissions(missing.toTypedArray(), REQ_CODE) // Implement your permission request logic here
    return
}
</code></pre>
<p>If an SDK call returns a <code>PERMISSION_REQUIRED</code> error, inspect <code>error.data</code> to identify the list of missing permissions. You should then request these permissions from the user and retry the original SDK call once they are granted.</p>
<h6>C. Use-case recipes</h6><p><img alt="Permission behavior changes sequence" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blt23ce855715bc349f/693994f49f57d67b0c2af9b9/Permission-behaviour-changes-sequence.png" /></p>
<p>Let's look at specific use cases and the permissions they require.</p>
<p><strong>1. Audio-only calling (Webex Call/meetings)</strong></p>
<ul>
<li><strong>Permissions:</strong> <code>RECORD_AUDIO</code></li>
<li><strong>Flow:</strong><ol>
<li>Check for and request microphone permission if not already granted.</li>
<li>Proceed to call <code>webex.phone.dial(...)</code> (or <code>answer(...)</code>).</li>
<li>If <code>PERMISSION_REQUIRED</code> is returned, prompt the user for the missing permission and retry the call.</li>
</ol>
</li>
</ul>
<br />

<pre><code class="language-kotlin">val mic = Manifest.permission.RECORD_AUDIO
if (ContextCompat.checkSelfPermission(ctx, mic) != PackageManager.PERMISSION_GRANTED) {
    // requestPermissions(arrayOf(mic), REQ_MIC) // Request microphone permission
    return
}
webex.phone.dial(address, MediaOption.audioOnly()) { result -&gt; /* handle call result */ }
</code></pre>
<p><strong>Important:</strong> <code>RECORD_AUDIO</code> is a runtime (dangerous) permission. You must always prompt the user for this permission at runtime on Android 6 (API 23) and higher.</p>
<p><strong>Manifest entries:</strong></p>
<pre><code class="language-xml">&lt;uses-permission android:name=&quot;android.permission.RECORD_AUDIO&quot; /&gt;
</code></pre>
<p><strong>2. Audio + Video calling</strong></p>
<ul>
<li><strong>Permissions:</strong> <code>RECORD_AUDIO</code>, <code>CAMERA</code> (plus optional <code>READ_PHONE_STATE</code> if enabled in your app)</li>
<li><strong>Flow:</strong> Request both <code>RECORD_AUDIO</code> and <code>CAMERA</code> permissions before attempting to dial or answer a video call.</li>
</ul>
<br />

<pre><code class="language-kotlin">val needed = arrayOf(Manifest.permission.RECORD_AUDIO, Manifest.permission.CAMERA)
// request if missing ... then
webex.phone.dial(address, MediaOption.audioVideo(/* views */)) { result -&gt; /* handle call result */ }
</code></pre>
<p><strong>Manifest entries:</strong></p>
<pre><code class="language-xml">&lt;uses-permission android:name=&quot;android.permission.RECORD_AUDIO&quot; /&gt;
&lt;uses-permission android:name=&quot;android.permission.CAMERA&quot; /&gt;
</code></pre>
<p><strong>3. Screen sharing (MediaProjection consent handoff)</strong></p>
<ul>
<li><strong>Permissions:</strong> No direct runtime permission string is required for MediaProjection itself; instead, you must obtain a consent intent.</li>
<li><strong>Flow:</strong><ol>
<li>Launch the screen capture intent using <code>MediaProjectionManager#createScreenCaptureIntent()</code>.</li>
<li>Upon successful user consent, pass the returned <code>data: Intent</code> to <code>call.startSharing(consentData, ...)</code> and proceed with the screen sharing operation.</li>
<li>If your UX includes overlays (e.g., for annotations), you must check <code>Settings.canDrawOverlays(...)</code> and, if necessary, guide the user to grant this permission in their device settings.</li>
</ol>
</li>
</ul>
<br />

<pre><code class="language-kotlin">val mgr = ctx.getSystemService(Context.MEDIA_PROJECTION_SERVICE) as MediaProjectionManager
val consentIntent = mgr.createScreenCaptureIntent()
launcher.launch(consentIntent)
// onActivityResult / ActivityResult callback:
call.startSharing(notification, notifId, data /* consent */, callback, shareConfig)
</code></pre>
<p><strong>Manifest entries:</strong></p>
<pre><code class="language-xml">&lt;!-- No runtime permission string for MediaProjection consent --&gt;
&lt;!-- If your UX includes overlays (e.g., annotations), and you actually present them: --&gt;
&lt;uses-permission android:name=&quot;android.permission.SYSTEM_ALERT_WINDOW&quot; /&gt;
</code></pre>
<p><strong>4. Audio routing (speaker, Bluetooth, earpiece)</strong></p>
<ul>
<li><strong>Permissions:</strong><ul>
<li><code>MODIFY_AUDIO_SETTINGS</code> (required for all audio routing operations – this is a normal permission)</li>
<li><code>BLUETOOTH_CONNECT</code> on API 31+ for Bluetooth headset toggling (this is a dangerous permission)</li>
<li>Legacy <code>BLUETOOTH</code> for older Android versions (if supporting them)</li>
</ul>
</li>
<li><strong>Flow:</strong> Declare <code>MODIFY_AUDIO_SETTINGS</code> in your manifest. Request Bluetooth permission at runtime if your app uses Bluetooth audio routing. Then, call <code>call.switchAudioOutput(...)</code>.</li>
</ul>
<p><strong>Important:</strong> Without <code>MODIFY_AUDIO_SETTINGS</code> declared in your manifest, attempts to toggle to speaker mode or any other audio route will fail, potentially resulting in no audio during calls.</p>
<pre><code class="language-kotlin">// Switch to speaker (only needs MODIFY_AUDIO_SETTINGS in manifest)
call.switchAudioOutput(Call.AudioOutputMode.SPEAKER) { result -&gt; 
    if (result.isSuccessful) {
        // Audio routed to speaker
    }
}
// Switch to Bluetooth (needs MODIFY_AUDIO_SETTINGS + runtime Bluetooth permission)
val bt = if (Build.VERSION.SDK_INT &gt;= 31) Manifest.permission.BLUETOOTH_CONNECT else Manifest.permission.BLUETOOTH
if (ContextCompat.checkSelfPermission(ctx, bt) == PackageManager.PERMISSION_GRANTED) {
    call.switchAudioOutput(Call.AudioOutputMode.BLUETOOTH_HEADSET) { /* handle result */ }
} else {
    // Request Bluetooth permission at runtime
}
// Switch to earpiece/phone
call.switchAudioOutput(Call.AudioOutputMode.PHONE) { /* handle result */ }
</code></pre>
<p><strong>Manifest entries:</strong></p>
<pre><code class="language-xml">&lt;!-- Required for ALL audio routing operations (normal permission - no runtime request needed) --&gt;
&lt;uses-permission android:name=&quot;android.permission.MODIFY_AUDIO_SETTINGS&quot; /&gt;
&lt;!-- Only if your app uses Bluetooth audio routing --&gt;
&lt;!-- API 31+ --&gt;
&lt;uses-permission android:name=&quot;android.permission.BLUETOOTH_CONNECT&quot; /&gt;
&lt;!-- Legacy (if supporting older targets) --&gt;
&lt;uses-permission android:name=&quot;android.permission.BLUETOOTH&quot; /&gt;
</code></pre>
<p><strong>Note:</strong> <code>MODIFY_AUDIO_SETTINGS</code> is a normal permission, meaning it only requires manifest declaration and does not need a runtime request. However, <code>BLUETOOTH_CONNECT</code> is a dangerous permission on API 31+ and <em>does</em> require a runtime request.</p>
<p><strong>5. Optional: READ_PHONE_STATE</strong></p>
<ul>
<li>Some applications utilize <code>READ_PHONE_STATE</code> to enhance the call experience on specific devices or carriers. This permission should be considered optional—request it only if your app genuinely benefits from its functionality.</li>
</ul>
<p>Example (only request if you need it):</p>
<pre><code class="language-kotlin">val phoneState = Manifest.permission.READ_PHONE_STATE
val isGranted = ContextCompat.checkSelfPermission(ctx, phoneState) == PackageManager.PERMISSION_GRANTED
if (!isGranted) {
    // requestPermissions(arrayOf(phoneState), REQ_READ_PHONE_STATE) // Request permission
}
</code></pre>
<p><strong>SDK toggle:</strong></p>
<ul>
<li>You can control the SDK's behavior regarding this permission with <code>Phone.enableAskingReadPhoneStatePermission(enable: Boolean)</code>.</li>
<li>The default setting is <code>true</code>. When your target SDK is 30 or higher, this permission helps the SDK check network state, allowing it to auto-tune performance during calls.</li>
</ul>
<pre><code class="language-kotlin">// If your app does not benefit from READ_PHONE_STATE, you can opt out
webex.phone.enableAskingReadPhoneStatePermission(false)
</code></pre>
<p><strong>Manifest entries:</strong></p>
<pre><code class="language-xml">&lt;uses-permission android:name=&quot;android.permission.READ_PHONE_STATE&quot; /&gt;
</code></pre>
<h6>D. Handling SDK errors consistently</h6><br />

<ul>
<li>If the SDK's preflight checks detect missing permissions, you will receive a <code>PERMISSION_REQUIRED</code> error, with a detailed list of the missing permissions provided in <code>error.data</code>.</li>
<li>Your application should then prompt the user to grant these permissions via your UI, and subsequently retry the exact API call that failed.</li>
<li>To avoid a confusing user experience, ensure that your app's UI and the SDK's preflight checks are aligned. You should prevent scenarios where the app displays a &quot;missing permission&quot; toast while allowing a separate flow to proceed, as this can lead to a confusing and broken user experience.</li>
</ul>
<br />

<h6>E. Flavor-level control for Play Store compliance</h6><br />

<ul>
<li>To optimize for Play Store compliance and reduce warnings, consider splitting your permission declarations by product flavor or module. This allows you to declare only the permissions that each specific build variant truly requires.</li>
<li>This approach helps in minimizing Play Console warnings associated with unused dangerous permissions, contributing to a smoother app submission process.</li>
</ul>
<br />

<h6>FAQ</h6><p><strong>We've compiled answers to some common questions you might have about these changes.</strong></p>
<h6>Does the SDK still show permission dialogs?</h6><p>No. With this release, all permission prompts are now app-owned. The SDK's role is to validate permissions and report <code>PERMISSION_REQUIRED</code> errors when they are missing.</p>
<h6>Do I need to change anything for 16 KB page size?</h6><p>No. For 16 KB page size support, simply updating to this SDK version is sufficient. No code changes are required on your part.</p>
<h6>Can the SDK return an error and still connect?</h6><p>No, not for the same operation. If a preflight check for permissions fails, the intended call or operation will not be executed. It's crucial to ensure your app's UI does not display an unrelated permission toast while allowing a separate flow to proceed, as this can lead to a confusing and broken user experience.</p>
<h6>Conclusion</h6><p>This release of the Webex Mobile SDK 3.16.0v marks an important step towards greater platform compatibility and developer flexibility. While the 16 KB memory page size support is a straightforward update, the transition to app-owned permission handling is a breaking change that requires careful migration. By following the detailed steps outlined in this guide, you can ensure your applications remain compliant with Google's latest requirements, provide a robust user experience, and leverage the full power of the Webex SDK. We encourage you to update your applications, thoroughly test the new permission flows, and enjoy the enhanced control this release provides. As always, the <a>Webex Developer Support Team</a> is happy to help with any issues or questions. You can also start or join a conversation about this topic on the <a href="https://community.cisco.com/t5/webex-for-developers/bd-p/disc-webex-developers" rel="noopener noreferrer" target="_blank">Webex for Developers Community Forum</a>. </p>
