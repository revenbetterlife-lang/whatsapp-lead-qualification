# WhatsApp Lead Qualification

An n8n workflow that connects WhatsApp and Odoo CRM to automate lead creation: when a customer sends a WhatsApp message, the workflow turns it into a CRM lead automatically, with no manual data entry.

## The workflow

1. **WhatsApp Trigger** - receives incoming WhatsApp messages.
2. **Is Text Message?** - checks whether the message is text.
3. **Extract Contact Info** - pulls out the customer's name, phone number, and message.
4. **Search Contact By Phone (Odoo)** - looks the contact up in Odoo CRM by phone number.
5. **Contact Exists?** - branches on whether the contact is already in the CRM.
6. **Create Contact (Odoo)** - creates a new contact when none exists.
7. **Use Partner ID** - picks the right Partner ID (existing or newly created).
8. **Create Lead/Opportunity (Odoo)** - creates a new Lead/Opportunity linked to that partner, with the message as the description.
9. **Send WhatsApp Confirmation** - sends the customer an automatic confirmation message.

## Who this helps

Any business that gets customer inquiries on WhatsApp and tracks them in a CRM: real estate, e-commerce, clinics and services, education and training, B2B sales teams, and lead-generation agencies. Every minute spent manually entering customer data is time that could be spent selling.

## Setup

1. Import `workflow.json` into n8n (Workflows, Import from File).
2. Add your credentials in n8n: WhatsApp Business Cloud API (trigger and send nodes) and Odoo (the three Odoo nodes).
3. Replace every `PASTE_CREDENTIAL_ID` / `PASTE_PHONE_NUMBER_ID` placeholder by selecting your real credentials on each node.
4. Activate the workflow and register its webhook URL in your WhatsApp Business app.

## Notes

- No real credentials, phone number IDs, or Odoo URLs are included in this repo; they all live in your own n8n credential store.
- The journey this builds: Customer Message to Contact to CRM to Lead to Follow-up.
- Built with n8n, the WhatsApp Business Cloud API, and Odoo CRM.
