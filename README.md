# FortifyNet for Claude

Audit your websites with [FortifyNet](https://fortifynet.com) and let Claude explain the results. Claude runs or fetches a FortifyNet security audit, explains the score and each finding in plain language, puts the fixes in order of severity and gives concrete steps for each one. MSPs and consultants can turn an audit into a client-ready summary with prioritised work items, and anyone can check uptime and monitoring alerts across their domains.

Everything Claude reports comes from your FortifyNet account through FortifyNet's connector. The skills tell Claude to use only what FortifyNet returns and never to make up findings, scores or numbers.

## What it does

The plugin adds three skills and FortifyNet's connector:

| Skill | Use it when you want to |
| --- | --- |
| `website-security-audit` | Run or read an audit of a domain and understand it: the score, each finding by severity, what it means and how to fix it |
| `security-report-for-client` | Turn an audit into a summary for a client or management, with prioritised work items and an effort estimate per item (no prices) |
| `monitoring-check` | See which sites are down, availability over a period, outages and recent monitoring alerts |

FortifyNet's audits cover SSL/TLS, DNS and email protection (SPF, DMARC and more), security headers, performance and leaked accounts, and depending on your plan, exposure, compliance, WHOIS and technology checks. Claude only reports the checks your audit actually ran.

## Requirements

- **A FortifyNet account.** Sign up at https://fortifynet.com.
- **The AI connection on your plan.** FortifyNet includes the AI connection (Claude, ChatGPT) in its Professional and Enterprise plans; see https://fortifynet.com/Pricing for the current plans. With a plan that does not include it, you can still sign in, and Claude tells you that the connection is not included.
- **Your domains added in FortifyNet.** Claude can audit domains that are in your account. You add domains in the FortifyNet app at https://fortifynet.com/Domains; the plugin cannot add them.
- **The FortifyNet connector, connected.** The plugin points at FortifyNet's MCP server, `https://fortifynet.com/api/mcp`. You connect it once and sign in with your FortifyNet account.

Starting an audit needs the owner or admin role in the FortifyNet organization. A viewer can read reports, uptime and alerts.

## Install and connect

1. Add the FortifyNet plugin from the plugin directory: on claude.ai under **Customize > Plugins**, or in Claude Code with `/plugin`.
2. Connect FortifyNet. On claude.ai and in Cowork, open the plugin's **Connectors** tab and connect FortifyNet. In Claude Code, the server loads with the plugin; run `/mcp` to sign in.
3. Sign in to FortifyNet in the window that opens, check the access request and select **Allow**.

To disconnect, remove the connector in Claude. Resetting your FortifyNet password, adding or removing a passkey, or setting up two-factor sign-in also ends every AI connection; connect again afterwards.

Setup guide on FortifyNet's site: https://fortifynet.com/AiConnect

## Examples

- "How secure is example.com? What should I fix first?"
- "Run a new FortifyNet audit of shop.example.com and explain the results in Swedish."
- "What does the DMARC finding in my latest report mean, and how do I fix it?"
- "Make a management-level security summary for my client acme.example, with work items and effort."
- "Turn the audits for all domains in the organization Example Dental into tickets."
- "Is any of my sites down right now? Show alerts from the last 7 days."
- "How was uptime for shop.example.com over the last 30 days?"

## Limits

FortifyNet sets the limits, and Claude passes them on when it hits one: an audit takes about a minute, one call starts at most five audits, and each account has an hourly and a daily audit limit. Each new audit is saved as a new report in your audit history. Claude can read your account but cannot add or remove domains, change settings, acknowledge alerts or see billing; the connector has no tools for that.

## Privacy Policy

FortifyNet's privacy policy: https://fortifynet.com/PrivacyPolicy

What data flows where:

- **The plugin itself** is a set of instructions (Markdown) and a reference to FortifyNet's server (JSON). It contains no code, stores nothing and sends nothing anywhere.
- **Claude and FortifyNet.** When you use a skill, Claude calls FortifyNet's MCP server at `https://fortifynet.com/api/mcp` with the OAuth token you granted when you signed in. FortifyNet answers with data from your account: your account's name and email address, your organizations and roles, your domains, audit scores and findings, uptime and monitoring alerts. Those answers become part of your Claude conversation, which Anthropic handles under its own terms and privacy policy.
- **Starting an audit.** When you ask for a new audit, FortifyNet audits your domain with the same services it always uses, as described in its privacy policy, and stores the report in your account.
- **Nothing else.** No data goes to any other service through this plugin.
- **Access.** The connection only reaches what your FortifyNet account can see, and only after you sign in and approve it. FortifyNet stores its tokens hashed. You can remove the connection in Claude at any time.

## Support

Email support@fortifynet.com. FortifyNet is published by Westnell Holding AB.

## License

MIT. See [LICENSE](LICENSE).
