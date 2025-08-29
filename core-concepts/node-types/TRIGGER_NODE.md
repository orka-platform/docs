---
title: 'Trigger Node'
icon: 'circle-play'
---

The Trigger Node is the fundamental starting point of every workflow in Orka. It defines how and when a workflow is initiated, serving as the entry point that determines the execution context and scheduling behavior.

<div align="left"><figure><img src="https://3431340728-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FsU4OKsizzEpCVNSoTs7U%2Fuploads%2F2uNqqii8yYLdBLAnDoCI%2FScreenshot%202025-08-22%20at%209.04.35%E2%80%AFPM.png?alt=media&#x26;token=add6d268-0dfc-43cf-b039-40dc5bb8f635" alt="" width="514"><figcaption></figcaption></figure></div>

## What is a Trigger Node?

A Trigger Node is a special workflow component that:

* Always appears first in workflow definitions
* Defines the execution method (manual or scheduled)

***

## Trigger Types

### <mark style="color:$primary;">1. Manual Trigger</mark>

The simplest trigger type that allows workflows to be executed on-demand.

### <mark style="color:$primary;">2. Scheduled Trigger</mark>

Advanced trigger type that enables automated, time-based workflow execution.

#### **Schedule Types**

1.  **Interval Schedule:** &#x20;

    Executes workflows at regular time intervals.

    _**Supported Units:**_

    _seconds - Execute every X seconds_

    _minutes - Execute every X minutes_

    _hours - Execute every X hours_

    _days - Execute every X days_



1.  **Weekly Schedule:**

    Executes workflows on specific days of the week at a designated time.

    _**Example:** Weekly every Monday at 9 AM._



    <div align="left"><figure><img src="https://3431340728-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FsU4OKsizzEpCVNSoTs7U%2Fuploads%2FXuf8hMLZOiot7KXTdfMT%2FScreenshot%202025-08-22%20at%208.50.40%E2%80%AFPM.png?alt=media&#x26;token=d59ee8bd-cfc7-4831-b0b5-551aba2ba325" alt=""><figcaption></figcaption></figure></div>



3.  **One-Time Schedule:**&#x20;

    Executes a workflow once at a specific date and time.

    _**Example:** Once on 30th of August 2025 at 08:52 PM._

    ![](https://3431340728-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FsU4OKsizzEpCVNSoTs7U%2Fuploads%2FUOMcHQAfGAYAF9WmtDdT%2FScreenshot%202025-08-22%20at%208.52.38%E2%80%AFPM.png?alt=media\&token=a2185931-a549-49f8-ae2c-c6355d7e66a1)



3.  **Cron Schedule:**&#x20;

    Executes workflows using standard cron expressions for complex scheduling patterns.

    _**Example:**_ **`0 0 1 * *`** _: First day of each month_
