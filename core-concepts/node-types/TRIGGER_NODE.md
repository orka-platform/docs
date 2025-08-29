---
title: 'Trigger Node'
icon: 'circle-play'
---

The Trigger Node is the fundamental starting point of every workflow in Orka. It defines how and when a workflow is initiated, serving as the entry point that determines the execution context and scheduling behavior.

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


2.  **One-Time Schedule:**&#x20;

    Executes a workflow once at a specific date and time.

    _**Example:** Once on 30th of August 2025 at 08:52 PM._


3.  **Cron Schedule:**&#x20;

    Executes workflows using standard cron expressions for complex scheduling patterns.

    _**Example:**_ **`0 0 1 * *`** _: First day of each month_
