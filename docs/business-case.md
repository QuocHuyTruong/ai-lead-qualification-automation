AI Lead Qualification & Routing Automation
Business Problem
Businesses that receive customer inquiries manually often spend unnecessary time reviewing every lead, deciding which prospects deserve attention, and copying their information into spreadsheets.
This creates several problems:
High-value leads may not be noticed quickly enough.
Staff must manually review repetitive inquiries.
Lead information can become inconsistent or scattered.
Sales teams spend time qualifying prospects instead of contacting the best opportunities.
Solution
I built an automated lead qualification workflow using n8n that receives new leads through a webhook and uses AI to evaluate each inquiry.
The system automatically classifies leads into three categories:
HOT — high-potential opportunity requiring immediate attention.
WARM — potentially valuable lead that should be followed up.
COLD — low-priority or low-value opportunity.
All leads are automatically recorded in Google Sheets, while HOT leads immediately trigger a Telegram notification so they can be handled quickly.
Workflow

1. Webhook — Receive Lead
   The workflow accepts lead information from an external application, website, form, or API.
2. Normalize Lead
   Incoming data is converted into a consistent structure before further processing.
   Typical information includes:
   Name
   Email
   Budget
   Project requirements
3. Gemini — Qualify Lead
   The lead information is sent to Gemini for analysis.
   The AI evaluates factors such as:
   Available budget
   Project requirements
   Project clarity
   Suitability for automation services
4. Parse AI Result
   The AI response is converted into structured data containing information such as:
   Classification
   Qualification score
   Reason for the classification
5. Route by Classification
   The workflow automatically routes the lead based on its AI classification:
   HOT → Immediate notification + storage
   WARM → Storage
   COLD → Storage
6. Google Sheets — Save Lead
   Every processed lead is automatically appended to Google Sheets, creating a simple centralized lead database.
7. Telegram — HOT Lead Alert
   When a lead is classified as HOT, the workflow immediately sends a Telegram notification containing the most important lead information.
   Business Value
   This workflow reduces the amount of manual lead qualification required from a sales team.
   Instead of:
   Receive lead → Read manually → Evaluate → Record data → Notify salesperson
   the process becomes:
   Receive lead → AI evaluates → Automatically stores → Alerts when important
   The sales team can therefore focus its attention on high-potential opportunities rather than repeatedly reviewing every incoming inquiry.
   Technology Stack
   n8n — workflow orchestration
   Gemini API — AI lead qualification
   Google Sheets API — lead storage
   Telegram Bot API — real-time HOT lead notifications
   Webhook / REST API — external lead intake
   JavaScript — AI response parsing and data processing
   Potential Applications
   The same workflow architecture can be adapted for:
   Marketing agencies
   Freelancers
   SaaS companies
   Real-estate businesses
   Consulting businesses
   Sales teams
   Service businesses
   CRM lead intake systems
   It can also be extended later with CRM integration, automated email follow-up, lead assignment, scheduling, dashboards, or additional business rules.
