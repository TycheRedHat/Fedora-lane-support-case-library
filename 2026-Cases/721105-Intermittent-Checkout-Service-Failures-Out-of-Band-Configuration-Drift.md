# Case #721105: Checkout Platform Outage (Undocumented Configuration Drift)



**Severity:** Severity 3 (Moderate)

**Opened By:** Casey Novak (Head of Linux Engineering)

**Status:** Closed



## Details of the Case

The production checkout platform experienced an unexpected service disruption lasting eight days. Red Hat Support and internal engineering engaged in a prolonged joint-troubleshooting effort to isolate the root cause. The extended Mean Time to Resolution (MTTR) was entirely due to a lack of centralized administrative audit logs. Once the root cause—an undocumented configuration change—was finally identified on October 14th, the change was reverted and service was restored in minutes.



## Solution Strategy

*   **Immediate Fix:** The undocumented configuration was reverted.

*   **Preventative Solution:** Enable RHEL's built-in **Session Recording (`tlog`)** and the **RHEL Web Console (Cockpit)** across critical infrastructure nodes. This requires no additional licensing and can be activated immediately.



## Possible Downstream Risks (If Unresolved)

*   **Extended Outages:** Future configuration drifts will continue to require days of manual reverse-engineering to locate.

*   **Compliance Audit Failures:** Un-audited administrative changes on financial or checkout platforms pose a direct threat to PCI DSS compliance standing.

*   **Shadow IT:** Lack of visibility prevents the organization from knowing who made changes, what was changed, and when.



## Learning Points

*   **Visibility Drives Resolution:** The outage wasn't prolonged by a complex technical failure, but by an administrative blind spot. 

*   **Maximize Existing Investments:** The tools needed to prevent this issue (Session Recording) are already included in the current RHEL subscription; they simply need to be turned on.

*   **Visual Auditing:** With Session Recording enabled, auditors and admins can visually play back terminal sessions to instantly see what broke a system, completely eliminating the guesswork.