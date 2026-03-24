---
type: reference
status: active
created: 2026-03-24
updated: 2026-03-24
domain: business
tags:
  - licensing
  - california
  - compliance
  - legal
  - business-operations
---

# California Licensing Requirements for Tech Consultants Serving Financial Firms

Last Updated: 2026-03-24

## Overview

Research into what licenses and registrations Advisor Intelligence needs to legally operate as a technology consultant serving RIA firms in California. Key finding: **technology consulting for financial firms does NOT require SEC/state investment adviser registration**, but standard California business licensing applies.

## Business License Requirements

### City/County Business License (Required)
- California has **no state-wide business license**
- You must obtain a business license from the **city or county where your business is primarily based**
- For San Diego: San Diego Business Tax Certificate (essentially a business license)
- Cost: Typically $34-$150/year depending on revenue and location
- Apply through the city's business licensing office or online portal

### DBA / Fictitious Business Name (If applicable)
- Required if operating under any name other than your legal name
- "Advisor Intelligence" requires a DBA filing if operating as sole proprietorship
- File with San Diego County Recorder's Office
- Cost: ~$26 filing fee + publication in local newspaper

### EIN (Recommended)
- Federal Employer Identification Number from IRS
- Free, obtained online at IRS.gov
- Required for LLC/Corp; recommended even for sole proprietors
- Needed for business bank accounts, processing 1099s from clients

### LLC Formation (Recommended)
- California LLC: File Articles of Organization with Secretary of State
- Cost: $70 filing fee
- Annual Franchise Tax: $800 minimum (this is the big one)
- Provides liability protection between personal and business assets

## Professional Licensing: NOT Required

### SEC/State Investment Adviser Registration
**Not required.** Advisor Intelligence does NOT provide investment advice. The service is:
- AI technology consulting and workflow automation
- Training advisors to use AI tools
- Building custom AI workflows
- This is technology consulting, not investment advisory

RIA registration is required for firms that **provide investment advice to clients for compensation** and **manage client assets**. Advisor Intelligence does neither.

### Key Distinction
- **What requires registration**: Providing investment advice, recommending specific securities, managing portfolios, providing financial planning advice
- **What does NOT require registration**: Technology consulting, software implementation, workflow automation, AI training, CRM configuration
- This is the same category as a Salesforce consultant, IT managed services provider, or compliance software vendor

### California-Specific Professional Licenses
The California Department of Consumer Affairs regulates ~40 categories of professionals. Technology/IT consulting is **not among them**. Categories that are regulated include:
- Real estate agents/brokers
- Insurance agents/brokers
- Accountants (CPA)
- Attorneys
- Contractors (CSLB)
- Engineers

**Technology consultants are not a regulated profession in California.**

## Insurance Requirements

### E&O / Professional Liability (Strongly Recommended)
- Not legally required, but **clients will likely require it**
- RIA firms and broker-dealers commonly require proof of E&O insurance from vendors
- See [[EO-Insurance-Research]] for detailed pricing and providers

### General Liability (Recommended)
- Covers third-party bodily injury and property damage
- Relevant if visiting client offices
- Many commercial leases require GL coverage
- Typical: $1M per occurrence / $2M aggregate

### Cyber Liability (Recommended)
- Especially important for tech consultants handling or accessing client systems
- Covers data breach costs, notification requirements, forensic investigation
- Can often be added as rider to GL or E&O policy
- Relevant given access to client Salesforce instances and email systems

### Workers' Compensation
- Required in California if you have employees
- Not required for sole proprietors/single-member LLC with no employees
- Can opt into coverage for yourself as business owner

## Tax Requirements

### California Franchise Tax
- LLC/Corp: $800 minimum annual franchise tax (regardless of revenue)
- Due by April 15
- First-year exemption for new LLCs (as of recent CA law changes — verify current status)

### Sales Tax
- Consulting services are generally **not subject to California sales tax**
- Software-as-a-service (SaaS) taxation in CA is complex but typically exempt for remote access
- The toolkit component of Advisor Intelligence (web-based templates) should be exempt
- If selling physical goods or certain digital products, a seller's permit is needed

### Income Tax
- Standard California income tax on business profits
- California Franchise Tax Board (FTB) for state
- IRS for federal
- Quarterly estimated tax payments required

## RIA-Adjacent Considerations

### Vendor Due Diligence
RIA clients will likely perform vendor due diligence, which may include:
- Proof of business registration
- Proof of insurance (E&O, GL, cyber)
- SOC 2 compliance (eventually — not needed at current scale)
- Written information security policy
- Business continuity plan

### Compliance Positioning
- Advisor Intelligence should maintain a clear boundary: **we consult on technology, not investments**
- Marketing copy should never imply investment advisory services
- Avoid language like "helping advisors make better investment decisions" — instead "helping advisors use AI tools more effectively"
- This aligns with existing [[Compliance-Framework]] positioning

### FINRA Considerations for Wirehouse Clients
- Wirehouse advisors (e.g., Morgan Stanley contacts) may face restrictions on using outside consultants
- FINRA-regulated firms typically require outside vendor approval through compliance
- Wirehouse engagement should be limited to personal coaching only (per [[Business-Model]])

## Action Items

1. **Immediate**: Obtain San Diego Business Tax Certificate
2. **Immediate**: File DBA for "Advisor Intelligence" if operating as sole proprietorship
3. **Immediate**: Get EIN from IRS (if not already done)
4. **Short-term**: Form LLC in California ($70 + $800 annual franchise tax)
5. **Short-term**: Obtain E&O insurance (see [[EO-Insurance-Research]])
6. **Short-term**: Obtain GL insurance
7. **Medium-term**: Add cyber liability coverage
8. **Medium-term**: Develop written information security policy for vendor due diligence

## Needs Further Investigation
- Confirm San Diego-specific business license requirements and fees
- Whether California's first-year LLC franchise tax exemption still applies
- Whether any specific San Diego home-based business permits are needed
- SOC 2 compliance timeline and cost (relevant as we scale to multiple clients)
- Whether DLK or other clients require specific insurance minimums

## Sources
- https://www.upcounsel.com/starting-a-consulting-business-in-california
- https://pedropaulobusinessconsultant.com/do-i-need-a-business-license-to-be-a-consultant-in-california/
- https://www.nolo.com/legal-encyclopedia/starting-consulting-business-california.html
- https://howtostartabusinesscalifornia.com/how-to-start-a-consulting-business-in-california/
- https://www.insureon.com/blog/do-business-consultants-need-certifications-and-licenses
- https://www.investopedia.com/articles/professionals/041013/becoming-registered-investment-advisor.asp
- CalGOLD (California Government: Online to Desktops) — license finder tool

## Related Notes
- [[EO-Insurance-Research]]
- [[Business-Model]]
- [[Compliance-Framework]]
- [[Business-Infrastructure]]
- [[DLK-HUB]]
