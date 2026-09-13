# What To Steal If You Are Not Us

You do not need to copy anyone's whole setup.

If you are using coding agents on real software, steal the pieces that make work
clearer and failure cheaper.

## 1. The Cold Start Test

Before implementation, ask whether a capable person or agent could execute the
work without the conversation that created it.

If not, keep shaping.

## 2. Out Of Scope

Name the tempting extras. This prevents helpfulness from becoming an
unreviewable diff.

## 3. Validation Plan

Separate what must be true from how you will prove it.

The validation plan should match your real runtime, whether that is a local app,
staging environment, mobile device, cloud account, or lab hardware.

## 4. Risk Tiers

Give low-risk work a fast path and high-risk work a human gate.

Do not let agents assign final risk for changes that can lock users out, leak
data, or mutate production.

## 5. Closeout

Close with evidence and follow-ons.

That habit turns every implementation into input for better future work.

## 6. Thin Agent Adapters

If you use multiple coding tools, avoid four different process files.

Keep one `AGENT_PROCESS.md`. Point each agent-specific file at it.

## Start Small

Add the template. Write one Work Order. Implement it. Learn from the closeout.

That is enough to begin.

The protocol only becomes powerful because the loop repeats.

