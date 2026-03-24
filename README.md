# Weekly Work Tracker → Slack Automation

Automates weekly status updates by converting structured entries in
Google Sheets into a formatted Slack summary.

Designed to remove the overhead of manual reporting while ensuring
consistent, structured communication.

------------------------------------------------------------------------

## Overview

This solution enables a simple workflow:

-   Log work incrementally throughout the week (\~2 minutes/day)
-   Automatically generate a structured summary
-   Deliver it to Slack at a scheduled time (e.g., Friday EOD)

The output includes: - Accomplishments - Blockers - Planned work for the
following week

------------------------------------------------------------------------

## Key Features

-   Automated weekly summary generation
-   Structured categorization of work items
-   Slack-native formatting using Block Kit
-   Time-based trigger (runs every Friday)
-   Minimal daily effort required

------------------------------------------------------------------------

## Architecture

Google Sheets → Apps Script → Slack Webhook

1.  Data is captured in a structured Google Sheet
2.  Apps Script processes the current week's entries
3.  A formatted payload is sent via Slack Incoming Webhook
4.  Execution is triggered automatically on a schedule

------------------------------------------------------------------------

## Setup

### 1. Google Sheet

Create a sheet with monthly tabs named:

Mar 2025\
Apr 2025

Each tab should contain weekly sections separated by divider rows:

WEEK 1 · Mar 3 -- Mar 7\
WEEK 2 · Mar 10 -- Mar 14

Data structure:

  Date   Task   Category   Status   Notes
  ------ ------ ---------- -------- -------

Supported categories: - accomplishment - blocker - next week

------------------------------------------------------------------------

### 2. Apps Script Configuration

Open: Extensions → Apps Script

Paste the script and update:

``` javascript
const CONFIG = {
  SLACK_WEBHOOK_URL : "YOUR_WEBHOOK_URL",
  YOUR_NAME         : "Your Name",
  SEND_HOUR         : 17
};
```

------------------------------------------------------------------------

### 3. Slack Webhook

1.  Create an Incoming Webhook in Slack
2.  Select the target channel
3.  Copy the webhook URL
4.  Add it to the script configuration

------------------------------------------------------------------------

### 4. Enable Scheduled Execution

Run the following once:

``` javascript
createFridayTrigger();
```

This schedules automatic execution every Friday at the configured time.

------------------------------------------------------------------------

### 5. Test Execution

``` javascript
testSendNow();
```

------------------------------------------------------------------------

## Output

The Slack message is structured into:

-   Accomplishments
-   Issues & Blockers
-   Planned Work

Each entry includes: - Status indicator - Task description - Optional
notes

------------------------------------------------------------------------

## Design Principles

-   Minimal daily friction
-   Consistent weekly reporting
-   Clear separation of work categories
-   Automation over manual effort

------------------------------------------------------------------------

## Use Cases

-   Weekly manager updates
-   Consulting status reporting
-   Personal productivity tracking
-   Team-level reporting extensions

------------------------------------------------------------------------

## Limitations

-   Assumes consistent sheet structure
-   Single-user workflow (by design)
-   Slack webhook required

------------------------------------------------------------------------

## Future Enhancements

-   Multi-user support
-   Notion / API integrations
-   Email delivery option
-   Dashboard visualization

------------------------------------------------------------------------

## Author

Guransh Deol

Focused on building lightweight systems that reduce operational overhead
and improve clarity.
