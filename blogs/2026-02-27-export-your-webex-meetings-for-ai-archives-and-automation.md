---
title: "Export Your Webex Meetings for AI, Archives, and Automation"
url: "https://developer.webex.com/blog/export-your-webex-meetings-for-ai-archives-and-automation"
date: "Fri, 27 Feb 2026 00:00:00 GMT"
author: "Adam Weeks"
feed_url: "https://developer.webex.com/blog/feed"
---
<img alt="Export Your Webex Meetings for AI, Archives, and Automation" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blt9cfeb5e0faf581a4/69a1ed08f9181e73f6ac62b3/export-your-webex-meetings-for-ai-archives-and-automation.png?width=900&amp;height=317&amp;fit=crop" /> <p>Ever finish a Webex meeting and think, &quot;I wish I could automatically save that recording, transcript, and AI summary somewhere useful&quot;? Maybe you want to feed meeting insights into an LLM, build a searchable company knowledge base, or just keep a clean archive without clicking through the web interface every time.</p>
<p>Today we're open-sourcing <strong>meetings-exporter</strong>—a Python CLI that does exactly that. Export everything from a Webex meeting into a tidy folder structure or straight to Google Drive, ready for your AI assistant to analyze.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="what-it-does-title"></a>What It Does</h4><a class="offset-anchor-tag" name="what-it-does"></a><p>meetings-exporter pulls together the full picture of your meetings:</p>
<ul>
<li><strong>Meeting details</strong> – Title, date, time, host, and participants</li>
<li><strong>Recordings</strong> – Video files (MP4, WebM, M4A) downloaded and saved locally</li>
<li><strong>Transcripts</strong> – VTT or plain text, ready for search or analysis</li>
<li><strong>AI summaries</strong> – Webex Meeting Summaries API output (summary text + action items)</li>
</ul>
<p>Each meeting gets its own folder, named like <code>2026-02-05 14-00 - Project Kickoff</code>, so everything sorts chronologically and stays easy to find.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="who-it39s-for-title"></a>Who It's For</h4><a class="offset-anchor-tag" name="who-it39s-for"></a><ul>
<li><strong>AI enthusiasts</strong> – Feed transcripts and summaries into <strong>Gemini, Claude, ChatGPT, or custom LLMs</strong> for post-meeting analysis, automated follow-ups, or knowledge extraction</li>
<li><strong>Compliance teams</strong> – Maintain compliant, searchable archives with local or cloud backups</li>
<li><strong>Automation engineers</strong> – Trigger exports programmatically—call <code>export_meeting()</code> from Python or use webhooks for zero-touch automation</li>
<li><strong>Integration builders</strong> – Extend with new backends (OneDrive, Slack, Dropbox) without touching core logic</li>
</ul>
<p>It's designed to be simple for quick one-off exports and flexible enough to plug into bigger systems—or your AI assistant's workflow.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="supercharge-your-ai-assistant-title"></a>Supercharge Your AI Assistant</h4><a class="offset-anchor-tag" name="supercharge-your-ai-assistant"></a><p>Imagine finishing a meeting and having Gemini, ChatGPT, or Claude instantly ready to:</p>
<ul>
<li><strong>Generate follow-up emails</strong> from the transcript and action items</li>
<li><strong>Extract key decisions</strong> and add them to your project tracker</li>
<li><strong>Answer questions</strong> like &quot;What did Sarah commit to in last week's meetings?&quot;</li>
<li><strong>Create stakeholder summaries</strong> without re-watching recordings</li>
<li><strong>Build a searchable knowledge base</strong> across all your team's meetings</li>
</ul>
<p>With meetings-exporter, your meeting data becomes <strong>AI-ready the moment the meeting ends</strong>. Export to Google Drive, point your AI assistant at the folder, and let it work its magic. No manual downloads, no copy-paste, no switching between tools.</p>
<p><strong>Example workflow:</strong></p>
<ol>
<li>Meeting ends → webhook triggers automatic export to Google Drive</li>
<li>Gemini reads <code>transcript.txt</code> and <code>summary.txt</code> from your Drive folder</li>
<li>You ask: &quot;What action items came out of this morning's sync?&quot;</li>
<li>Gemini responds with a clean list, complete with context and owners</li>
</ol>
<p>The same workflow works with ChatGPT's file uploads, Claude's Projects feature, or any custom RAG pipeline you build.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="before-you-start-title"></a>Before You Start</h4><a class="offset-anchor-tag" name="before-you-start"></a><ul>
<li>Python 3.11+ installed (we use modern type hints and <code>tomllib</code>)</li>
<li>A <a href="https://www.webex.com/" rel="noopener noreferrer" target="_blank">Webex account</a> with meeting history</li>
<li>Your <a>Personal Access Token</a></li>
<li>(Optional) A Google Cloud project for Drive exports</li>
</ul>
<p><strong>⚠️ Security Note:</strong> Personal Access Tokens grant full access to your Webex account. Never commit <code>.env</code> to version control. For production use, consider using OAuth or a service account with scoped permissions.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="quick-start-title"></a>Quick Start</h4><a class="offset-anchor-tag" name="quick-start"></a><pre><code class="language-bash">git clone https://github.com/WebexSamples/meetings-exporter.git
cd meetings-exporter
python3 -m venv .venv &amp;&amp; source .venv/bin/activate
pip install -e &quot;.[dev]&quot;
cp env.template .env
# Edit .env and set WEBEX_ACCESS_TOKEN
</code></pre>
<p><strong>List your recent meetings:</strong></p>
<pre><code class="language-bash">meetings-exporter list --from 2026-02-01 --to 2026-02-28 --max 10
</code></pre>
<p><strong>Export a single meeting to a local folder:</strong></p>
<pre><code class="language-bash">meetings-exporter export MEETING_ID --output-dir ./exports
</code></pre>
<p><strong>Export all meetings in a date range:</strong></p>
<pre><code class="language-bash">meetings-exporter export --from 2026-02-01 --to 2026-02-28 --output-dir ./exports
</code></pre>
<p>No Google or cloud setup is required for local export—just your Webex token.</p>
<p><strong>Note:</strong> The Webex APIs have rate limits. When exporting large date ranges, the tool automatically throttles requests. For very large archives (100+ meetings), consider running overnight or in batches.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="webhook-server-autoexport-on-events-title"></a>Webhook Server: Auto-Export on Events</h4><a class="offset-anchor-tag" name="webhook-server-autoexport-on-events"></a><p>When your meeting ends, Webex POSTs a JSON payload to your webhook server. The tool extracts the meeting ID, acknowledges the event instantly (so Webex doesn't retry), then exports everything in the background—no manual intervention required.</p>
<p><strong>How it works:</strong></p>
<ol>
<li>Run <code>meetings-exporter webhook --port 8080</code> and expose it via <a href="https://ngrok.com" rel="noopener noreferrer" target="_blank">ngrok</a> (or another tunnel) so Webex can reach it.</li>
<li>Register webhooks with Webex: <code>meetings-exporter webhook register --url https://your-ngrok-url.ngrok-free.app</code></li>
<li>When a meeting ends, a recording is created, or a transcript is ready, Webex POSTs to your <code>/webhook</code> endpoint.</li>
<li>The server responds with 200 immediately, then runs <code>export_meeting()</code> in a background thread.</li>
<li>The full export runs—meeting details, participants, recordings, transcript, summary—and writes to your configured backend (local folder or Google Drive).</li>
</ol>
<p><strong>Events we listen for:</strong></p>
<ul>
<li><code>meetings.ended</code> – Meeting has ended</li>
<li><code>recordings.created</code> – Recording is available for download</li>
<li><code>meetingTranscripts.created</code> – Transcript is ready</li>
</ul>
<p>You can optionally set <code>WEBEX_WEBHOOK_SECRET</code> in <code>.env</code> to verify the <code>X-Spark-Signature</code> header and reject forged requests. When done testing, run <code>meetings-exporter webhook unregister</code> to remove the webhooks.</p>
<p><strong>Troubleshooting Webhooks:</strong></p>
<ul>
<li><strong>Ngrok URL changes?</strong> Re-run <code>webhook register</code> with the new URL</li>
<li><strong>Not receiving events?</strong> Check <code>meetings-exporter webhook list</code> to verify registration</li>
<li><strong>Export failing silently?</strong> Check server logs—background threads don't print errors to console by default. Run with <code>--log-level DEBUG</code> for detailed output.</li>
</ul>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="export-to-google-drive-title"></a>Export to Google Drive</h4><a class="offset-anchor-tag" name="export-to-google-drive"></a><p>If you prefer cloud storage (and want your AI assistant to access it), configure <code>EXPORT_BACKEND=google_drive</code> and your Google OAuth credentials in <code>.env</code>. The same folder structure (meeting details, transcript, summary, recordings) is uploaded to Drive. You can optionally set <code>GOOGLE_DRIVE_FOLDER_ID</code> to target a specific folder.</p>
<p>This makes it trivial to grant Gemini, ChatGPT, or your custom AI agent read access to all your meeting data—just share the Drive folder.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="what-you-get-title"></a>What You Get</h4><a class="offset-anchor-tag" name="what-you-get"></a><p>Each exported meeting produces a folder like this:</p>
<pre><code>2026-02-05 14-00 - Q1 Planning Session/
  meeting_details.txt   # Title, date, host, participants
  transcript.vtt        # Or transcript.txt
  summary.json          # Raw Meeting Summaries API response
  recording_1.mp4       # 45 minutes, 1080p
</code></pre>
<p>Everything is normalized and ready for downstream tools—or your AI assistant. The <code>summary.json</code> gives you the full Meeting Summaries API payload if you want to build custom parsers or integrations.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="how-we-built-it-title"></a>How We Built It</h4><a class="offset-anchor-tag" name="how-we-built-it"></a><p>meetings-exporter is built on two Webex API families. Here's what we use and where to find the docs.</p>
<h6>Webex Meetings API</h6><p>The <a>Webex Meetings API</a> gives us meeting metadata, participants, recordings, and transcripts. We call these endpoints:</p>
<ul>
<li><strong><a>List Meetings</a></strong> – Lists past meetings in a date range. We use <code>meetingType=meeting</code> so we only get individual instances (series don't support transcripts or summaries).</li>
<li><strong><a>Get a Meeting</a></strong> – Fetches title, start/end time, host, and other metadata for a single meeting.</li>
<li><strong><a>List Meeting Participants</a></strong> – Returns attendees with display names and emails for <code>meeting_details.txt</code>.</li>
<li><strong><a>List Recordings</a></strong> – Lists recordings for a meeting (IDs, host email, format).</li>
<li><strong><a>Get Recording Details</a></strong> – Returns <code>temporaryDirectDownloadLinks.recordingDownloadLink</code>, a pre-signed CDN URL for the actual video file. We use this (not <code>downloadUrl</code>, which points to a web page) to download the MP4/WebM/M4A binary.</li>
<li><strong><a>Meeting Transcripts</a></strong> – Lists transcripts for a meeting. We use the <code>txtDownloadLink</code> from each item to download the VTT or plain-text content.</li>
</ul>
<h6>Meeting Summaries API</h6><p>The <a>Meeting Summaries API</a> provides AI-generated summaries and action items:</p>
<ul>
<li><strong><a>Get Summary by Meeting ID</a></strong> – Returns the summary text and action items for a meeting. We write the summary to <code>summary.txt</code> and the full JSON response to <code>summary.json</code>.</li>
</ul>
<h6>Architecture</h6><p>We fetch all of this via a single <code>WebexClient</code>, normalize it into a <code>MeetingData</code> model, and pass it to pluggable exporters (local folder or Google Drive). The design makes it straightforward to add OneDrive, Dropbox, or other backends without changing the ingestion logic.</p>
<p><strong>⚠️ Important:</strong> Summaries, recordings, and transcripts are available only for <strong>individual meeting instances</strong> (IDs like <code>abc123_I_xyz789</code>), not recurring series. Series IDs won't return this data. The tool filters for instances automatically when listing meetings, but if you manually pass a series ID to <code>export</code>, the export will be incomplete. Always export instance meetings, not series.</p>
<p>Contributions are welcome—see <a href="https://github.com/WebexSamples/meetings-exporter/blob/main/CONTRIBUTING.md" rel="noopener noreferrer" target="_blank">CONTRIBUTING.md</a> for setup and code style.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="get-started-now-title"></a>Get Started Now</h4><a class="offset-anchor-tag" name="get-started-now"></a><ol>
<li><strong>Clone the repo:</strong> <code>git clone https://github.com/WebexSamples/meetings-exporter.git</code></li>
<li><strong>Export your first meeting</strong> in under 5 minutes</li>
<li><strong>Connect your AI assistant</strong> to the export folder and start asking questions about your meetings</li>
<li><strong>Built something cool?</strong> Share it in the <a href="https://community.cisco.com/t5/collaboration/ct-p/collaboration" rel="noopener noreferrer" target="_blank">Webex Developer Community</a>—we'd love to feature your project!</li>
</ol>
<p>The repo lives at <a href="https://github.com/WebexSamples/meetings-exporter" rel="noopener noreferrer" target="_blank">github.com/WebexSamples/meetings-exporter</a>. Whether you're building an AI-powered meeting assistant, maintaining compliance archives, or just want your data in one place—meetings-exporter makes it simple.</p>
