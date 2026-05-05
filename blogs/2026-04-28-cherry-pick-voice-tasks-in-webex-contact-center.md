---
title: "Cherry-Pick Voice Tasks in Webex Contact Center"
url: "https://developer.webex.com/blog/cherry-pick-voice-tasks-in-webex-contact-center"
date: "Tue, 28 Apr 2026 00:00:00 GMT"
author: "Taylor Hanson"
feed_url: "https://developer.webex.com/blog/feed"
---
<img alt="Cherry-Pick Voice Tasks in Webex Contact Center" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blt305f8e972656a03d/69f1146a5ff35984608f6f04/cherry_pick_banner.jpg?width=900&amp;height=317&amp;fit=crop" /> <p>In contact centers, sometimes supervisors or agents need a way to see what is waiting in the queue and pull the right call instead of relying on automatic distribution. This is necessary in Hospital Transfer Centers where a nurse may need to connect multiple inbound calls from clinicians.</p>
<p>In this post, we will walk through a small Agent Desktop widget that does exactly that for Webex Contact Center: displays queued voice calls and uses the Get Tasks and Assign Task APIs so an agent can cherry-pick a call.</p>
<h6>What the widget does</h6><p>The project hosts a custom widget intended to run inside Contact Center Agent Desktop. A queue flow can notify the widget server side when new phone contacts arrive (optional but recommended for responsiveness). The widget uses the Contact Center APIs to list tasks the agent has access to and to assign a chosen task. Together, that gives the end user a practical pattern for “see the queue, pick the call” experiences where the queue and multimedia profile policies support manual assignment.</p>
<h6>How to get started</h6><p>The full source for this proof of concept is <a href="https://github.com/wxsd-sales/wxcc-voice-cherry-picker" rel="noopener noreferrer" target="_blank">on GitHub</a>. For API details, start with the official <a>task call-control documentation</a> for Webex CC.</p>
<ol>
<li><strong>Manual assignment must be allowed</strong><br />For Get/Assign behavior to work as expected for voice, your service queue and the agent’s multimedia profile (MMP) need manuallyAssignable configured appropriately (queue-level flag and MMP telephony manual assignment). The repository <a href="https://github.com/wxsd-sales/wxcc-voice-cherry-picker?tab=readme-ov-file#3-update-the-queue-and-mmp-manuallyassignable-properties" rel="noopener noreferrer" target="_blank">README</a> describes the shape of those settings; many teams apply them with an API client such as Postman or Bruno rather than in the widget code itself.</li>
</ol>
<ol start="2">
<li> <strong>Optional flow hook for faster UI updates</strong><br />If you only rely on polling, new tasks appear on a several second interval. To push calls to the widget sooner, add an HTTP Request node in your queue flow POSTs to your widget server’s public URL with a JSON body containing the contact fields  described <a href="https://github.com/wxsd-sales/wxcc-voice-cherry-picker?tab=readme-ov-file#2-configure-the-cc-queue-flow" rel="noopener noreferrer" target="_blank">here</a>.</li>
</ol>
<ol start="3">
<li><strong>Running the sample</strong><br />Clone the repository, copy .env.example to .env, set PORT (for example 5000) and HOST_URI to the base URL where the server will be reachable (<a href="http://localhost:5000" rel="noopener noreferrer" target="_blank">http://localhost:5000</a> for local dev, or <a href="https://your.server.com" rel="noopener noreferrer" target="_blank">https://your.server.com</a> in production).</li>
</ol>
<p>Full setup instructions can be found <a href="https://github.com/wxsd-sales/wxcc-voice-cherry-picker?tab=readme-ov-file#1-set-up-the-env-file" rel="noopener noreferrer" target="_blank">here</a>.</p>
<h6>See it in action</h6><p>For a quick overview of behavior and setup, checkout the <a href="https://app.vidcast.io/share/1ec61338-9263-4e20-95c7-87cb24dfbdf3" rel="noopener noreferrer" target="_blank">Vidcast</a>!</p>
<h6>In closing</h6><p>If you are extending Contact Center with custom desktop experiences, this sample is a compact reference for task discovery, assignment, and flow-to-widget signaling. If you have questions about Webex APIs or SDKs, you can reach developer support at <a href="mailto:devsupport@webex.com" rel="noopener noreferrer" target="_blank">devsupport@webex.com</a>. For questions about this WXSD sales engineering sample specifically, use <a href="mailto:wxsd@external.cisco.com" rel="noopener noreferrer" target="_blank">wxsd@external.cisco.com</a>.</p>
