# Awesome-Salesforce-CRM-Billing-Integration

# Awesome Salesforce CRM Billing Integration

> A curated list of top Salesforce CRM Billing Integration platforms — both SaaS/Hosted commercial connectors and open-source alternatives for syncing subscriptions, invoices, and payments between Salesforce and billing systems.
> 🌟 Star this repo if you find it useful! 🌟

---

## 📋 Table of Contents

- [SaaS / Hosted Platforms](#-saas--hosted-platforms)
  - [Chargebee for Salesforce](#chargebee-for-salesforce)
  - [Chargebee CPQ for Salesforce](#chargebee-cpq-for-salesforce)
  - [MuleSoft Anypoint Salesforce Connector](#mulesoft-anypoint-salesforce-connector)
  - [Celigo Salesforce Connector](#celigo-salesforce-connector)
  - [Workato Salesforce Recipe](#workato-salesforce-recipe)
  - [Jitterbit Salesforce](#jitterbit-salesforce)
  - [Boomi Salesforce Connector](#boomi-salesforce-connector)
- [Open-Source Software](#-open-source-software)
  - [salesforce-stripe-payment-processing](#salesforce-stripe-payment-processing)
  - [SFDC-MaxioAB-Integration](#sfdc-maxioab-integration)
  - [Delivery Hub](#delivery-hub)
  - [Twenty (Salesforce Alternative)](#twenty-salesforce-alternative)
- [Comparison at a Glance](#-comparison-at-a-glance)
- [Contributing](#-contributing)

---

## 🟦 SaaS / Hosted Platforms

Commercial, cloud-hosted Salesforce CRM Billing Integration platforms. These are not open-source but are included as reference points for feature comparison.

### Chargebee for Salesforce
**Type:** Native billing sync with customizable field mapping
Chargebee's Salesforce integration maintains a one-to-one relationship between Chargebee customers and Salesforce accounts, keeping both systems synchronized . Key capabilities include:
- Creating and managing Chargebee subscriptions directly from Salesforce without switching tools 
- Multiple Chargebee sites connected to a single Salesforce instance 
- Support for Metered Billing, Multi-decimal Pricing, and Quantities 
- A **sync health dashboard** for at-a-glance status and **record-level sync logs** for complete audit trails 
- Advanced field-mapping configuration between Salesforce and Chargebee 

The integration is configured entirely within Salesforce, with customizations available to suit specific business workflows . Sync frequencies range from every 10 minutes to daily .
**Best for:** Subscription businesses already using Chargebee wanting native, bi-directional sync of customers, subscriptions, and invoices within Salesforce.

### Chargebee CPQ for Salesforce
**Type:** CPQ quoting with Chargebee's pricing engine
Chargebee CPQ brings advanced quoting capabilities to Salesforce, letting sales teams create quotes within Salesforce while leveraging Chargebee's product catalog and pricing engine . Features include:
- **Ramps** for ramped pricing structures over time 
- **Multi-Frequency Billing** combining products with different billing frequencies in one quote 
- **Access Control** for field-level permissions on quote fields 

**Important limitation:** CPQ integration cannot operate concurrently with the standard Chargebee for Salesforce integration . Quote creation automatically creates a Chargebee customer if one doesn't exist for the linked Salesforce Account .
**Best for:** Sales teams needing CPQ-level quoting with Chargebee's catalog and pricing, accepting that it replaces the standard Salesforce integration.

### MuleSoft Anypoint Salesforce Connector
**Type:** Enterprise iPaaS with certified Salesforce connector
MuleSoft provides a certified Salesforce connector within its Anypoint Platform, enabling integration between Salesforce and billing systems (Chargebee, Stripe, NetSuite, etc.) through DataWeave transformations and API-led connectivity. Suited for enterprises with complex, multi-system billing workflows requiring governance and reusability.

### Celigo Salesforce Connector
**Type:** Integration platform with pre-built Salesforce flows
Celigo offers pre-built connectors and integration apps for Salesforce, including flows for billing platforms. Its marketplace includes accelerators for order-to-cash and quote-to-cash processes, making it suitable for organizations wanting managed integration apps rather than custom development.

### Workato Salesforce Recipe
**Type:** Enterprise automation with Salesforce recipes
Workato provides pre-built recipes connecting Salesforce to billing platforms, with triggers and actions for customer sync, subscription creation, and invoice updates. Suited for organizations wanting automation with governance and audit trails.

### Jitterbit Salesforce
**Type:** iPaaS with Salesforce and billing connectors
Jitterbit Harmony provides reusable connectors for Salesforce alongside billing platform connectors, with API management and EDI capabilities. Suited for organizations needing unified integration across CRM, billing, and partner systems.

### Boomi Salesforce Connector
**Type:** Cloud-native iPaaS with Salesforce connectivity
Boomi offers a pre-built Salesforce connector with visual mapping and data transformation, enabling integration between Salesforce and billing systems. Positioned for mid-market organizations wanting a proven iPaaS without enterprise complexity.

---

## 🟩 Open-Source Software

Self-hosted, community-driven Salesforce Billing Integration tools. The open-source ecosystem is **limited**—available projects focus on specific billing platforms (Stripe, Maxio) or provide broader Salesforce-native alternatives.

### salesforce-stripe-payment-processing
**Stack:** Apex (Salesforce) | **License:** Open Source (per GitHub)
A robust Salesforce (Apex) integration with **Stripe** for payment processing, supporting both inbound (webhook) and outbound (API callout) events . Key features include:
- **Inbound Webhook Handling:** Processes Stripe events (customer updates, subscription changes, invoice payments) via a REST resource 
- **Outbound Stripe API Integration:** Creates and updates Stripe customers, products, prices, and checkout sessions from Salesforce 
- **Secure Secrets:** Stores Stripe API keys in Salesforce custom metadata 
- **Asynchronous Processing:** Uses Queueable Apex for non-blocking, scalable interactions 
- **Comprehensive Tests:** Includes test data factories and HTTP callout mocks 

Architecture includes a `WebhookResource` for Stripe webhooks, a `StripeAPIClient` for outbound callouts, and Queueable classes for async operations. Setup requires configuring Stripe secret keys in Custom Metadata, Named Credentials, Remote Site Settings, and Stripe webhook endpoints .
**Best for:** Salesforce developers wanting a production-ready, Apex-native Stripe integration with webhook handling and secure credential storage, avoiding external middleware.

### SFDC-MaxioAB-Integration
**Stack:** Python (AWS Lambda) / Apex | **License:** Open Source (per GitHub)
An AWS Lambda function that integrates Salesforce with **Maxio Advanced Billing (AB) and Core** . It processes closed-won opportunities in Salesforce and creates corresponding customer records, component price points, and subscriptions in Maxio, then establishes a relationship from Maxio AB to Maxio Core . Features include:
- Retrieves Salesforce Opportunity, Quote, Order, and Consumption Schedule data via OAuth 2.0 
- Creates/updates Maxio customers and generates custom pricing tiers from Salesforce consumption schedules 
- Creates subscriptions with appropriate components and price points 
- Stores results in Snowflake for persistence and retrieval 

**Trade-off:** Requires AWS Lambda, Salesforce, Maxio AB/Core, and Snowflake accounts, making it a multi-service integration rather than a simple connector.
**Best for:** Organizations using Maxio for billing needing a Lambda-based bridge from Salesforce opportunities to Maxio subscriptions with Snowflake persistence.

### Delivery Hub
**Stack:** Apex / Lightning Web Components (Salesforce) | **License:** Open Source (per project)
Delivery Hub is a free, open-source Salesforce-native managed package that bundles document generation, invoice generation, and automation in one pipeline . Key billing-related features include:
- **Invoice Generation:** One-click PDF invoices from Work Items or Projects, with line items pulling automatically from approved Work Logs (sums hours by rate, applies tax, calculates total) 
- **Optional QuickBooks Integration:** Bidirectional sync of invoices and payments, so when QuickBooks records a payment the Work Item closes automatically; reverse flow supports credit memos and refunds 
- **Invoice Lifecycle:** Draft → Generated → Sent → Paid → Closed 

The package ships with 150 Apex classes, 58 Lightning Web Components, and 89%+ test coverage . It explicitly positions itself as replacing DocuSign, Conga/FormStack, external invoicing tools, and Zapier/n8n for delivery workflows .
**Best for:** Salesforce-native consultancies and service businesses wanting invoice generation with QuickBooks sync without paying for separate billing or document tools.

### Twenty (Salesforce Alternative)
**Stack:** TypeScript / NestJS / React / PostgreSQL | **License:** AGPL-3.0
Twenty is a modern open-source CRM positioned as a Salesforce alternative, with **built-in billing automation** capabilities directly inside the CRM workflow . It integrates with Stripe for payment processing and offers a GraphQL API for custom integrations . Billing features let teams manage subscriptions, invoices, and payment collection without stitching together separate tools . Self-hostable via Docker with PostgreSQL, or available as a cloud-hosted version.
**Best for:** Teams wanting an open-source CRM with native billing features baked in, rather than integrating Salesforce with a separate billing platform.

---

## 📊 Comparison at a Glance

| Software | License | Stack | Billing Platform | Sync Direction | Self-Hosted | Best For |
|----------|---------|-------|------------------|----------------|-------------|----------|
| **Chargebee for Salesforce** | Proprietary | Cloud | Chargebee | Bi-directional | ❌ | Native Chargebee + Salesforce |
| **Chargebee CPQ** | Proprietary | Cloud | Chargebee | Salesforce → Chargebee | ❌ | CPQ quoting with Chargebee |
| **MuleSoft** | Proprietary | Cloud | Any (via connector) | Bi-directional | ❌ | Enterprise iPaaS |
| **Celigo** | Proprietary | Cloud | Any (pre-built flows) | Bi-directional | ❌ | Managed integration apps |
| **salesforce-stripe-payment-processing** | Open Source | Apex | Stripe | Bi-directional | ✅ (In-org) | Apex-native Stripe integration |
| **SFDC-MaxioAB-Integration** | Open Source | Python/Apex | Maxio | Salesforce → Maxio | ✅ (Lambda) | Maxio bridge + Snowflake |
| **Delivery Hub** | Open Source | Apex/LWC | QuickBooks | Bi-directional | ✅ (In-org) | Invoice generation + QB sync |
| **Twenty** | AGPL-3.0 | TypeScript | Stripe (built-in) | N/A (CRM) | ✅ | CRM with native billing |

---

## 🤝 Contributing

Contributions are welcome! If you know of an open-source Salesforce CRM Billing Integration tool that should be listed here, please open a pull request with:

- Project name and URL
- Brief description (1–2 sentences)
- Stack and license
- Why it stands out

Please ensure the project is actively maintained (releases within the last 12 months) and genuinely open-source. Note that the open-source ecosystem for **Salesforce billing integration** is fragmented across specific platform bridges (Stripe, Maxio) and Salesforce-native alternatives (Delivery Hub, Twenty) rather than general-purpose connectors. **salesforce-stripe-payment-processing** is the most complete open-source Apex-native Stripe integration, handling both webhooks and outbound API calls with secure credential storage . **Delivery Hub** is notable for bundling invoice generation with QuickBooks sync directly inside Salesforce at no cost . For production-grade multi-platform integration, commercial iPaaS connectors (MuleSoft, Celigo, Boomi) or native billing platform integrations (Chargebee) remain the standard choices.

---

## 📄 License

This list is released under CC0 1.0 Universal (Public Domain). The software projects listed retain their respective licenses.

---

⭐ **If this list helped you discover a useful tool, please star the repo!** ⭐
