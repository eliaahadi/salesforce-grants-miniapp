# Risks and tradeoffs

## Flow vs Apex
- Prefer Flow for maintainability
- Use Apex for complex orchestration or integration error handling

## Record visibility complexity
- Grants can require strict access controls; early security design reduces rework
- Conservative OWD + sharing rules can increase admin complexity

## Integration coupling
- Avoid point-to-point; middleware reduces coupling and centralizes reliability patterns

## Data volume growth
- Plan archiving strategy for historical applications and attachments
- Use async/batch patterns for heavy processes