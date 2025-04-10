<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build Your First AI Workflow

**Project Link:** [View Project](http://learn.nextwork.org/projects/ai-agent-nocode)

**Author:** Albert  
**Email:** tapcyberx@gmail.com

---

## Building an AI Workflow

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_sdrjg8e123dv)

---

## Introducing Today's Project!

In this project, I’ll demonstrate how to build an AI-powered workflow using n8n (no-code). I’ll show how sending a simple text can automatically schedule events in Google Calendar—making task automation effortless with AI.

### Tools and Techniques

In this project, I used n8n, Ollama (Llama 3.1), and Google Calendar. I learned how to build AI workflows, the difference between workflows and agents, how to use credentials, JSON expressions, and how to read AI logs to fix issues.

### Project reflection

This project took me a couple of days, with about 3 hours of work. The hardest part was fixing expression errors in the system message. The best part was seeing how much impact a well-tuned system message had on the workflow.



I did this project to get hands-on experience with AI automation and workflows, and to start understanding how AI agents work. It definitely exceeded my goals—I was able to set up a working prototype and see it in action.










---

## Exploring n8n

n8n is a workflow automation tool. In this project, we use it to build workflows—sequences of actions that complete tasks. AI enhances workflows by automating decisions, like using generative AI to draft email replies.










We signed up for free trial for n8n, which includes 14 days of access to n8n and the ability to create up to 5 workflows. We don't need to enter credit card details to start the trial, so we won't be charged.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_c9d8f7a2)

---

## Starting an AI Workflow

A workflow trigger is the event that starts a workflow. In this project, our trigger is a chat message, but other triggers can be a scheduled time (e.g., every day at 8 AM) or a manual activation.

An AI agent is an intelligent system that can independently perceive its environment, process information, and take actions to achieve goals. Unlike simple automation, it can make context-aware decisions without rigid, predefined steps.

In our project, we integrated an AI agent node into a structured workflow. While the overall process uses predefined triggers (for reliability), the agent handles dynamic decision-making where flexibility is needed.

Key Implementation:

Structured Trigger initiates the workflow (e.g., user input)

AI Agent takes over for adaptive tasks (e.g., routing requests based on content)

Controlled Autonomy balances predictability with intelligent handling

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_fmtkjyrg)

---

## Integrating ChatGPT

An AI workflow has three key components: Chat Model (the brain that processes inputs), Memory (stores past interactions and data), and Tools (software or code that helps execute tasks efficiently).










My workflow's chat model runs on Ollama locally, using the Llama 3.1 model for processing inputs and generating responses efficiently.t

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_o5p6q7r8)

---

## Integrating Google Calendar

In this workflow, the tool is Google Calendar, as it connects our AI agent to the API that creates new events. Tools help the AI interact with external services to complete tasks.

To connect with Google Calendar, we give n8n permission to create and edit events and calendars in our account. For security, it’s best to delete these credentials once the workflow is no longer needed.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_c9d8dfgv2)

---

## Testing My Workflow

When testing my AI workflow by asking to book a meeting for tomorrow at 10 AM, it created the event at the wrong time and returned an error: [ERROR: fetch failed], meaning it couldn’t properly reach the calendar API.

In this step, I reviewed the AI agent’s logs to troubleshoot the issue. The logs showed that the calendar tool received no input, meaning it wasn’t getting the correct start or end time to create the event.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_c9d8egrfdv)

---

## JSON Expressions

I decided to troubleshoot by reviewing the Calendar tool’s setup. I found an error in the start and end time settings—it was using the current time by default, ignoring the input from the chat model.










I updated the Calendar tool by setting the start and end times to use JSON references from the AI model. For example, the start time is now {{ $fromAI('start_time') }}, allowing the AI to pass accurate scheduling info.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_897rg465e)

---

## System Messages

On my second test, the workflow created an event using input from the AI chat model, but it scheduled the wrong date. The issue was the chat model passing incorrect date values to the Calendar tool.










A system message is a prompt sent to the AI agent before the conversation begins. It gives the agent clear instructions and context—like the current date—to help it respond more accurately.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_rfgdhn456)

---

## Success!

I updated the system message to use an expression instead of a fixed value. This way, the AI agent automatically receives the correct current date with each message, helping it schedule events accurately.

![Image](http://learn.nextwork.org/delighted_indigo_timid_orc/uploads/ai-agent-nocode_w3x4y5z6)

---

## System Message Variation

---

---
