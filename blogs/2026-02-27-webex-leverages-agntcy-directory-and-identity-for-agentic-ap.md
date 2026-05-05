---
title: "Webex Leverages AGNTCY Directory and Identity for Agentic Apps"
url: "https://developer.webex.com/blog/webex-leverages-agntcy-directory-and-identity-for-agentic-apps"
date: "Fri, 27 Feb 2026 00:00:00 GMT"
author: "Kriti Jain"
feed_url: "https://developer.webex.com/blog/feed"
---
<img alt="Webex Leverages AGNTCY Directory and Identity for Agentic Apps" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blt71d57bc0fdc81539/69a1b5d6c461dbdad26a256f/banner.png?width=900&amp;height=317&amp;fit=crop" /> <p>Enterprises are accelerating their use of artificial intelligence (AI) assistants and agentic workflows across both employee collaboration and customer service operations. Whether it’s an agent that autonomously troubleshoots a network via Meraki APIs or a virtual project manager that updates Jira tickets based on a Webex meeting summary, the Webex ecosystem is the premier destination for enterprise-grade agents.</p>
<p>Building a scalable, enterprise-grade agentic platform enables Webex products and services to operate as both providers and consumers of AI-driven capabilities. Webex platform leverages open agentic standards such as Model Context Protocol (MCP), Agent2Agent (A2A), and <a href="https://agntcy.org/" rel="noopener noreferrer" target="_blank">AGNTCY</a> (a Linux Foundation project founded by Outshift by Cisco), to help enterprises deploy trusted, interoperable, and collaborative AI agents at scale.</p>
<p>Building on our earlier collaboration with AGNTCY to pilot a multi-vendor, multi-agent collaboration for a <a href="https://outshift.cisco.com/blog/webex-agntcy-multi-agent-systems" rel="noopener noreferrer" target="_blank">healthcare contact center use case</a>, Webex has now integrated AGNTCY directory and identity components into its Agent Central Service (ACS) to enable trusted discovery and authentication of agentic apps (starting with MCP servers) onboarded to Webex developer portal and Webex App Hub. </p>
<h6>Webex Developer Portal and App Hub: Agentic integration</h6><p>The <a>Webex Developer Portal</a> is a unified platform providing APIs, SDKs, and tools that enable developers to build apps for Webex Suite (meetings, messaging, calling) and Contact Center, whereas the <a href="https://apphub.webex.com/" rel="noopener noreferrer" target="_blank">Webex App Hub</a> is the Webex marketplace for discovering and distributing agentic apps. The <strong>AGNTCY Directory service</strong> provides a standardized capability for registration, search, and resolution of various agentic resource records across the Webex ecosystem for both internal and external agentic services. While the <strong>AGNTCY Identity service</strong> issues verifiable credential issuance, validates signatures, and provides interoperable agentic resources’ identity resolution to enable trusted authentication and interoperability across ecosystems. </p>
<p>Integrating these capabilities in the Webex platform delivers the following key benefits:</p>
<ul>
<li><strong>Common governance and security layer:</strong> Single governance framework instead of separate controls per product or integration—reducing risk, compliance complexity, and operational overhead.</li>
<li><strong>Agentic interoperability:</strong> Webex products and external AI agents can discover, call, and collaborate with each other. It supports external agent / MCP server consumption and Webex agents / MCP servers' invocation.</li>
<li><strong>Discoverability and market exchange:</strong> Customers can activate approved agents/tools on demand instead of building from scratch. This improves time to market and enables ecosystem choice, innovation, and future extensibility.</li>
</ul>
<br />

<h6>Architecture</h6><br />

<h6>Agent Central Service</h6><p>The <strong>Webex Agent Central Service (ACS)</strong> is the governance and discovery backbone of the Webex Agentic Ecosystem. It provides a trusted, scalable, and developer-friendly foundation for registering, certifying, and managing agentic servers. </p>
<p>ACS now integrates AGNTCY directory and identity components for registration, discovery, and verification of internal and external MCP servers. This integration allows ACS to function as the enterprise governance control plane while leveraging AGNTCY’s open, interoperable agent infrastructure.</p>
<p>ACS introduces governance and compliance controls over all registered agentic servers—whether internal or third party—ensuring that only verified and policy-compliant servers participate within the ecosystem. It supports both MCP and A2A server registration (future) and enables their publication through the App Hub marketplace. </p>
<p>These server records are internally stored in AGNTCY directory service in a standardized <strong>Open Agent Schema Framework</strong> (<a href="https://docs.agntcy.org/oasf/open-agentic-schema-framework/" rel="noopener noreferrer" target="_blank">OASF</a>) format providing for skills-based discovery, content addressed records for integrity, and verifiable claims for recording signing and verification. </p>
<p>ACS uses the AGNTCY identity as the central hub for managing and verifying digital identities for agentic apps. The AGNTCY identity service is used to issue agent badges during agent app registration and then subsequently to verify the badges upon use. Identity badges are classified as:</p>
<ul>
<li><strong>Cisco Official</strong> (Certified by Cisco)</li>
<li><strong>Cisco Onboarded</strong> (Developed by XYZ; Certified by Cisco)</li>
<li><strong>Developer/partner Onboarded</strong> (Developed by XYZ; Reviewed by Cisco)</li>
<li><strong>Federated through external registry</strong> (Developed by XYZ; Imported from external registry)</li>
</ul>
<br />

<h6>Control Hub</h6><p>Through Control Hub integration, administrators can define and enforce enterprise policies across registered servers and internal agentic functions. These policies are automatically applied to all consumers of the ecosystem, including the Webex Agentic Client SDK and Webex Agentic Server, ensuring consistent governance and compliance enforcement.</p>
<p>The Client SDK, used internally by Webex products, leverages ACS for secure access to policy-enforced servers and functions supporting MCP and A2A use cases.</p>
<p>Additionally, ACS integrates with the Developer Portal to onboard agentic servers from partners and third-party developers, maintaining a continuously updated registry accessible to all ecosystem participants.</p>
<p><img alt="Agentic Servers on Dev Portal" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blt8a528b7f5c601a87/69a1b5d66f394b02aad848b7/Agentic_Servers_on_Dev_Portal.png" /></p>
<h6>How it works</h6><p>If you are a developer ready to bring your agent to the world, here is your roadmap for onboarding via the Webex Developer Portal and App Hub.</p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="1--developer-portal-onboarding-title"></a>1 . Developer Portal Onboarding</h4><a class="offset-anchor-tag" name="1--developer-portal-onboarding"></a><p>Register an Agentic Server (MCP/A2A) for use within an organization and optionally for public listing. </p>
<p>User will open Developer Portal and click on start building Apps. Once the user clicks on new Agentic App and fills metadata (name, description, server URL, module, auth type). Click on submit and new Agentic App is created. User can optionally submit for App Hub Approval.</p>
<p><img alt="Agentic App" src="https://images.contentstack.io/v3/assets/bltd74e2c7e18c68b20/blte4d0867ea62f42e2/69a1b5d6c461dbd2656a256b/Agentic_App.jpg" /></p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="2-app-hub-marketplace-title"></a>2. App Hub Marketplace</h4><a class="offset-anchor-tag" name="2-app-hub-marketplace"></a><p>By onboarding your agentic app onto the Webex App Hub, you aren't just publishing a tool—you are joining a secure, resilient ecosystem designed for the future of work.</p>
<p>Watch a video that demonstrates the workflow up to here: <a href="https://app.vidcast.io/share/55e8ee6f-aea4-404b-8114-35c180417563" rel="noopener noreferrer" target="_blank">Vidcast</a></p>
<h4><a class="anchor-tag icon icon-link_16 icon-link" name="3-provisioning-through-control-hub-title"></a>3. Provisioning through Control Hub</h4><a class="offset-anchor-tag" name="3-provisioning-through-control-hub"></a><p>Control Hub is used for provisioning. In the Control Hub section, once the user goes to Apps section and clicks on Agentic Apps, they can view a list of Agentic Apps. Server details will have tabs for:</p>
<ul>
<li><strong>Overview:</strong> Discover Agentic Servers (public and org-private) for an org admin.</li>
<li><strong>Tools:</strong> View server metadata and tool inventory. Enable/disable the MCP server at org/group scope.</li>
<li><strong>Auth configuration:</strong> Enable/disable and select enabled tools per server. Provide access to limit set of users.</li>
<li><strong>Custom parameters:</strong> Configure server auth parameters and custom parameters.</li>
</ul>
<p>Watch a video that demonstrates this workflow: <a href="https://app.vidcast.io/share/e5fe2e70-39a4-4b50-9998-36f2b769f253" rel="noopener noreferrer" target="_blank">Vidcast</a></p>
<h6>Future Outlook</h6><p>Looking ahead, Webex plans to leverage additional AGNTCY directory and identity services capabilities to enable: </p>
<ul>
<li>Policy-based, automatic federation of agent records from external agent registries such as the Anthropic MCP Server registry. This allows partners to register and sync their agent records to the Webex developer portal and app hub in a trusted and automated manner and Webex agent users to access a broad set of trusted, up-to-date agent apps that they can use in their agentic workflows. </li>
<li>Run-time agent resource discovery and record ingestion. This allows Webex users to automatically discover and register running agent resources they created in Webex to the ACS agent registry (powered by AGNTCY directory). This helps keep the agent records up to date for more accurate agent discovery and set-up of granular access control permissions on agent tools, skills, and capabilities.</li>
</ul>
<p>In addition to these AGNTCY capabilities, Webex is also looking to add support for A2A client and registration of agents in addition to the support for MCP servers today. </p>
<h6>Getting started</h6><p>Ready to start building? Head over to the <a>My Apps page</a> to register your first agentic app today. Join the <a href="https://community.cisco.com/t5/webex-for-developers/bd-p/disc-webex-developers" rel="noopener noreferrer" target="_blank">Webex Developer Community</a> and let’s build the future of Connected Intelligence together.</p>
<p>To learn more about AGNTCY, visit the <a href="https://github.com/agntcy" rel="noopener noreferrer" target="_blank">AGNTCY GitHub</a>. You can also use <a href="https://github.com/agntcy/dir" rel="noopener noreferrer" target="_blank">Directory</a>, <a href="https://github.com/agntcy/identity" rel="noopener noreferrer" target="_blank">Identity</a>, and <a href="https://github.com/agntcy/observe" rel="noopener noreferrer" target="_blank">Observe</a> to enable interoperable multi-agent discovery, authentication, authorization, and observability.</p>
