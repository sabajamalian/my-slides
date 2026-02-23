---
title: "Choosing an Enterprise Type for GitHub Enterprise Cloud"
theme: black
revealOptions:
  transition: slide
  backgroundTransition: fade
---

<!-- .slide: data-background="linear-gradient(135deg, #0d1117 0%, #161b22 40%, #1a1a4e 100%)" -->

# Choosing an Enterprise Type

### GitHub Enterprise Cloud

<br>

*Decide between two enterprise models — weighing identity, security, collaboration, and operational tradeoffs* <!-- .element: style="opacity:0.6; font-size:0.75em" -->

Note: This deck walks through the key questions GitHub recommends when choosing between an enterprise with personal accounts and an enterprise with managed users. Based on the official GitHub docs at docs.github.com/en/enterprise-cloud@latest/enterprise-onboarding/getting-started-with-your-enterprise/choose-an-enterprise-type.

---

<!-- .slide: data-background="#1a1a2e" -->

## Enterprise Options Overview

<div class="two-col" style="margin-top:1em;">

<div>

### 👤 Personal Accounts

<ul>
<li class="fragment fade-right" data-fragment-index="1">Users keep their <strong>own GitHub.com accounts</strong></li>
<li class="fragment fade-right" data-fragment-index="2">Optional <strong>SAML SSO</strong> integration</li>
<li class="fragment fade-right" data-fragment-index="3">Users create, manage, and sign in to their own accounts</li>
<li class="fragment fade-right" data-fragment-index="4">Flexibility and simplicity</li>
</ul>

</div>

<div>

### 🏢 Managed Users (EMU)

<ul>
<li class="fragment fade-left" data-fragment-index="1">Accounts <strong>provisioned by the company</strong></li>
<li class="fragment fade-left" data-fragment-index="2">Identity system <strong>controls access and profiles</strong></li>
<li class="fragment fade-left" data-fragment-index="3">Users authenticate via company IdP</li>
<li class="fragment fade-left" data-fragment-index="4">Strict control and security</li>
</ul>

</div>

</div>

Note: These are the two enterprise types available in GitHub Enterprise Cloud. The choice is fundamentally about how much control your organization needs over user identities and access.

---

<!-- .slide: data-background="#16213e" -->

## Do You Want to Control User Accounts?

<div class="two-col" style="margin-top:1em;">

<div>

### 🏢 Managed Users

<ul>
<li class="fragment fade-right" data-fragment-index="1"><strong>True SSO experience</strong> for users</li>
<li class="fragment fade-right" data-fragment-index="2">You <strong>provision accounts</strong> for your users</li>
<li class="fragment fade-right" data-fragment-index="3">You <strong>control usernames and email addresses</strong></li>
<li class="fragment fade-right" data-fragment-index="4">Users authenticate with your IdP using <strong>SAML or OIDC</strong></li>
</ul>

</div>

<div>

### 👤 Personal Accounts

<ul>
<li class="fragment fade-left" data-fragment-index="1">Users <strong>create, manage, and sign in</strong> to their own accounts</li>
<li class="fragment fade-left" data-fragment-index="2">SAML links personal account to <strong>enterprise identity</strong></li>
<li class="fragment fade-left" data-fragment-index="3"><strong>User provisioning is not available</strong></li>
<li class="fragment fade-left" data-fragment-index="4">SCIM can only provision <strong>access to individual organizations</strong></li>
</ul>

</div>

</div>

Note: If you currently require users to create new personal accounts on GitHub.com to contribute to your company's resources, EMU might be a better alternative. Consider personal accounts if using your external identity management system as the source of truth would add too much complexity — for example, you don't have an established process for onboarding new users in the system.

---

<!-- .slide: data-background="#0f3460" -->

## Do You Need to Choose Where Data Is Stored?

<div class="callout" style="margin-top:1em;">
💡 GitHub Enterprise Cloud includes the option to store your enterprise's code and data in a <strong>specific region</strong>.
</div>

<br>

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🌍</span>
<span>Regional data storage to help meet <strong>compliance requirements</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">🔗</span>
<span>Uses a dedicated <strong>GHE.com subdomain</strong> for your enterprise</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">⚠️</span>
<span>Data residency <strong>requires Enterprise Managed Users</strong></span>
</div>

<br>

<div class="callout warn fragment fade-up" data-fragment-index="4">
If data residency is a requirement, your only option is Enterprise Managed Users.
</div>

Note: GitHub Enterprise Cloud with data residency lets you store code and data in a specific region on your own subdomain of GHE.com. See GitHub's docs on "About GitHub Enterprise Cloud with data residency" for full details.

---

<!-- .slide: data-background="#1a1a2e" -->

## Is Your Identity Management System Supported?

<div class="two-col" style="margin-top:1em;">

<div>

### 🏢 Managed Users

<ul>
<li class="fragment fade-right" data-fragment-index="1"><strong>"Paved-path" integrations</strong> with supported identity providers (authentication + provisioning)</li>
<li class="fragment fade-right" data-fragment-index="2">Other identity systems allowed <strong>if they meet GitHub's guidelines</strong></li>
</ul>

</div>

<div>

### 👤 Personal Accounts

<ul>
<li class="fragment fade-left" data-fragment-index="1">Any external identity system that adheres to the <strong>SAML 2.0 standard</strong></li>
<li class="fragment fade-left" data-fragment-index="2">Some systems are <strong>officially tested and supported</strong> by GitHub</li>
</ul>

</div>

</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="3">
💡 Check whether you already use — or can adopt — a supported identity management system before deciding.
</div>

Note: For managed users, GitHub partners with specific identity management system developers to provide "paved-path" integrations that include both authentication and provisioning. For personal accounts, the requirements are simpler — any SAML 2.0 compliant provider will work. See "About Enterprise Managed Users" and "Configuring SAML single sign-on for your enterprise" in GitHub docs for the full list of supported providers.

---

<!-- .slide: data-background="#16213e" -->

## Do You Need Public Repos, Gists, or GitHub Pages?

Enterprise Managed Users imposes **strong restrictions** to prevent accidental leaks of corporate content: <!-- .element: style="font-size:0.95em" -->

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🚫</span>
<span>Cannot create <strong>public repositories</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">🚫</span>
<span>Cannot create <strong>gists of any visibility</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">🚫</span>
<span>Cannot create GitHub Pages sites <strong>visible outside the enterprise</strong></span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="4">
✅ If public content, open-source contributions, or external GitHub Pages are needed → <strong>choose personal accounts</strong>
</div>

Note: These restrictions are by design — to prevent enterprise members from accidentally leaking corporate-owned content to the public. Review the full list of restrictions in GitHub's docs under "Abilities and restrictions of managed user accounts" and confirm they won't hinder your existing workflows.

---

<!-- .slide: data-background="#0f3460" -->

## Do You Require Collaboration Outside Your Enterprise?

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🔒</span>
<span><strong>Managed user accounts</strong> can only contribute to repositories <strong>within your enterprise</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">🔀</span>
<span>External collaboration requires maintaining a <strong>separate personal account</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">⚠️</span>
<span>Regularly switching between accounts can increase the risk of <strong>mistakenly leaking internal code to the public</strong></span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="4">
✅ <strong>Personal accounts</strong> allow contribution across organizations and the broader GitHub ecosystem without restrictions
</div>

Note: If your developers must contribute to repositories outside of your enterprise — including private repositories — Enterprise Managed Users may not be right for you. The dual-account workflow is documented in "Getting started with Enterprise Managed Users" under "Support developers with multiple user accounts."

---

<!-- .slide: data-background="#1a1a2e" -->

## Can Your Enterprise Tolerate Migration Costs?

<div class="callout warn" style="margin-top:1em;">
⚠️ This applies if you <strong>already</strong> have an enterprise using personal accounts on GitHub.com
</div>

<br>

<div class="icon-text fragment fade-up" data-fragment-index="1">
<span class="icon">🔄</span>
<span>Adopting EMU requires migration to a <strong>new enterprise account</strong></span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="2">
<span class="icon">⏱️</span>
<span>The migration process may require <strong>time and cost</strong> from your team</span>
</div>

<div class="icon-text fragment fade-up" data-fragment-index="3">
<span class="icon">💬</span>
<span>Contact <strong>GitHub's Sales team</strong> to discuss the migration process</span>
</div>

<br>

<div class="callout fragment fade-up" data-fragment-index="4">
💡 Confirm that this migration process is acceptable to your business and your users before committing. If not, <strong>personal accounts</strong> may be the better choice.
</div>

Note: Moving from personal accounts to EMU is not a simple toggle — it requires a new enterprise account and a full migration process. Evaluate the business impact, timeline, and cost before switching. Reach out to GitHub's Sales team at enterprise.github.com/contact to discuss specifics.

---

<!-- .slide: data-background="#16213e" -->

## Decision Summary

| Requirement | Best Fit |
|---|---|
| Full identity control + strict security | **Managed Users** |
| Simpler onboarding and flexibility | **Personal Accounts** |
| Data residency required | **Managed Users** |
| Public repos, gists, or external collaboration | **Personal Accounts** |
| Low migration overhead | **Personal Accounts** |
| Prevent accidental data leaks | **Managed Users** |

Note: This is a simplified decision matrix. In practice, many organizations weigh multiple factors. The key is to evaluate your requirements for identity control, data residency, public content needs, external collaboration, and migration tolerance together rather than in isolation.

---

<!-- .slide: data-background="linear-gradient(135deg, #1a1a4e 0%, #2d1b69 50%, #0d1117 100%)" -->

## Next Steps

<ol class="action-plan">
<li class="fragment fade-up" data-fragment-index="1"><strong>Choose your enterprise type</strong> — personal accounts or managed users</li>
<li class="fragment fade-up" data-fragment-index="2"><strong>Start a GitHub Enterprise trial</strong> — set up and validate before committing</li>
<li class="fragment fade-up" data-fragment-index="3"><strong>Validate identity provider setup</strong> — confirm your IdP integration works</li>
<li class="fragment fade-up" data-fragment-index="4"><strong>Review EMU restrictions with engineering</strong> — ensure workflows are compatible</li>
</ol>

<br>

<div class="callout fragment fade-up" data-fragment-index="5">
📖 Full reference: <em>docs.github.com/en/enterprise-cloud@latest/enterprise-onboarding</em>
</div>

Note: Steps 1 and 2 are directly from GitHub's docs — after choosing an enterprise type, start a trial. Steps 3 and 4 are best-practice recommendations to de-risk the decision. See "Setting up a trial of GitHub Enterprise" in GitHub's docs for trial setup instructions.
