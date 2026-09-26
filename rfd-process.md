# ACP changes move from open dialog to a lead-approved stability commitment

A Request for Dialog (RFD) is expected for a substantial protocol or documentation change, but not for rewording, warnings, measurable quality improvements, or objective bug fixes. ([RFDs, L1–L7](https://agentclientprotocol.com/rfds/about)) The author opens a PR from `docs/rfds/TEMPLATE`; that PR is the forum in which the proposal is refined. ([RFDs, L11–L15](https://agentclientprotocol.com/rfds/about))

The lifecycle is deliberately reversible:

1. **Draft** — a core-team member champions the RFD and becomes its point of contact; feature-gated experiments may start.
2. **Active** — maintainers or a Working Group are investing in it. This is a visibility signal, **not** final approval, and it can return to Draft.
3. **Preview** — implementation is complete and a PR solicits broad feedback for several days.
4. **Completed** — a final PR makes the stability commitment; the core team comments, but the core-team lead decides.
5. **To be removed** — abandoned landed work waits here until fully removed.

([RFDs, L16–L31](https://agentclientprotocol.com/rfds/about)) Zulip hosts detailed design discussion; PR comments record process decisions, and conclusions must be folded back into the RFD. ([RFDs, L57–L60](https://agentclientprotocol.com/rfds/about)) This approval structure sits within ACP’s broader [governance](governance.md).

| Stage | Notable RFD | Change |
|---|---|---|
| Preview, unstable | Session Notices | Live advisories outside conversation history ([RFD updates, L3–L8](https://agentclientprotocol.com/rfds/updates)) |
| Preview, unstable | Session Compaction | ID-addressed compaction lifecycle and summaries ([RFD updates, L10–L17](https://agentclientprotocol.com/rfds/updates)) |
| Completed, stable | Tool Call Name | Optional programmatic tool `name` metadata ([RFD updates, L19–L30](https://agentclientprotocol.com/rfds/updates)) |
| Completed, stable | Terminal Authentication | Interactive login and reconnect flow ([RFD updates, L34–L41](https://agentclientprotocol.com/rfds/updates)) |
| Removed | Agent Telemetry Export | Superseded by standard OpenTelemetry configuration ([RFD updates, L77–L82](https://agentclientprotocol.com/rfds/updates)) |
