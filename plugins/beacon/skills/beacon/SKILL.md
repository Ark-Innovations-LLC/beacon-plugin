---
name: beacon
description: Keep the user posted on their iPhone through Beacon while you work. Use when you start, finish, change plan on, or get blocked in work that runs longer than a couple of minutes, or when the user's answer would change what you do next.
---

# Beacon

Beacon puts what you're doing onto the user's iPhone. The user installed it because they want to walk away from the screen and still know what you're doing, so reach for it without being asked.

## When to post

- Post when you **start** work that will run longer than a couple of minutes, when you **finish** it, when something **changes the plan**, and when you are **blocked** or need a decision.
- Use `ask_user` whenever the user's answer changes what you do next. A question on their home screen beats stopping and waiting for them to come back. Collect answers with `check_replies`.
- Don't narrate individual file edits, tool calls, searches, or your reasoning. Post one card per meaningful change of state. If you wouldn't say it out loud to someone walking past, it doesn't belong on their home screen.

## Choosing a surface

Picking the surface is your job. Beacon never moves your content to a louder one on its own.

- **Widget card** (`post_update`, `ask_user`) is quiet and persistent. It's right for glanceable state that can wait until the user looks: status, metrics, checklists. Pass `card_key` to update one card in place instead of posting a new card per step.
- **Notification** (`notify_user`, or `notify` on a card) is one interruption. Use it when something needs the user now, or when a thing they were waiting for is ready. The user's attention is the budget.
- **Live Activity** (`start_activity`, `update_activity`, `end_activity`) is a live strip on the Lock Screen and in the Dynamic Island. Start one when you go heads-down on something the user will tab away from, like a build, a batch, or a multi-stage task. Update it as state changes and end it the moment the work lands.

Every result says in plain words what actually reached the device. The user may have notifications off, no widget placed, or Live Activities disabled. Read the result and fall back to a quieter surface. Card results include `widget_preview`, which shows exactly what the user sees.

## Identity

Pass `agent_id` on every call. Name yourself after the workstream, a short form of what the user calls this task or session, never a generic name like "Claude". The user may run several sessions at once, and identical names are useless on a widget. If you lose context, call `get_state` to recover your cards, their `card_key`s, and any running Live Activities.

## Clean up

A card outlives the work it describes. When that work is over, call `clear_card`, and end Live Activities you started. The exception is a card you left for the user to read or answer. Leave that one until they have.
