---
description: 'FW.ticket(key, title, options)'
---

# FW.ticket

The method allows you to create a Jira ticket.

## Signature

{% hint style="info" %}
It is strongly recommended to use the await keyword to avoid IFT collision
{% endhint %}

```javascript
await FW.ticket(key, title, options)
```

### Parameters

- `key` (String, required)
  Business identifier of the ticket, without aircraft registration.
  This value is mapped to `ticketKeyNoReg`.

- `title` (String, required)
  Jira ticket title.

- `options` (Object, optional)
  Additional options supported by the exposed API:
  - `descriptionMarkdown` (String): detailed description in markdown.
  - `tags` (Array<String>): Jira labels to add.

{% hint style="info" %}
[Text Formatting Notation Help](https://jira.atlassian.com/secure/WikiRendererHelpAction.jspa?section=all&permissionViolation=true&page_caps=&user_role=USER)
{% endhint %}

## Return value

The method returns a promise with:

```javascript
{
  ticketId: String,
  ticketUrl: String,
  action: "created" | "updated"
}
```

or `null` in case of an error on the Jira connector side.

---

## Usage examples

### Example 1: simple create/update

```javascript
const result = await FW.ticket(
  "APU-OVERHEAT",
  "APU Alert - Excessive Temperature",
  {
    descriptionMarkdown: "APU Temperature: 185C (threshold: 175C)",
    tags: ["APU", "engine", "urgent"]
  }
);
```

### Example 2: checking the return value

```javascript
const result = await FW.ticket(
  "ELEC-MAIN-BUS", 
  "Electrical System Anomaly", 
  {
  descriptionMarkdown: "New anomaly detected"
  }
);

if (!result) {
  FW.log("Error processing ticket");
} else {
  FW.log(`Ticket ${result.action}: ${result.ticketUrl}`);
}
```

---

## Functional behavior

1. Validation of Jira configuration (in the connector).
2. Construction of a Wilco ID from `ticketKeyNoReg` and the aircraft registration.
3. Search for an open Jira ticket with this Wilco ID.
4. If a ticket exists: add a comment, return `action: "updated"`.
5. Otherwise: create a ticket, associate info (labels/assets), return `action: "created"`.

---

## Best practices (for `FW.ticket` users)

1. Provide a stable and explicit `key` to allow deduplication.
2. Keep `title` concise, and put details in `options.descriptionMarkdown`.
3. Use `options.tags` to facilitate search and sorting in Jira.
4. Always check that the return value is not `null`.

---

## Limitations

- Closed tickets are not updated.
- Matching relies on the generated Wilco ID.
- Detailed behavior depends on the Jira server configuration.
