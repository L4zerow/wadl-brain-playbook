# Phase 4: Build Checklist

## Pre-Work
- [ ] Architecture Doc reviewed
- [ ] Domain Spec accessible
- [ ] Development environment set up
- [ ] Access to all data sources confirmed
- [ ] Team roles assigned

## Data Layer Implementation
- [ ] API connections established
- [ ] Data ingestion scripts written
- [ ] Transformations implemented
- [ ] Storage configured
- [ ] Refresh mechanism built
- [ ] Data validation in place
- [ ] Initial data load completed
- [ ] Data quality verified

## Domain Layer Implementation (Cortex)

### Structure
- [ ] Core rule written
- [ ] Identity section written
- [ ] Available resources documented
- [ ] Schema reference inserted

### Business Rules
- [ ] All rules from Domain Spec encoded
- [ ] Examples included
- [ ] Anti-patterns documented
- [ ] Terminology section complete

### Known Entities
- [ ] All entities hardcoded
- [ ] IDs verified against source

### Query Templates
- [ ] Common query templates included
- [ ] Tested for correctness

### Guardrails
- [ ] Safety constraints implemented
- [ ] Output limits defined
- [ ] Forbidden operations listed

### Response Format
- [ ] Format locked in
- [ ] Formatting rules documented
- [ ] Include/exclude rules specified

### Validation
- [ ] Cortex reviewed against Domain Spec
- [ ] All business rules present
- [ ] All anti-patterns present
- [ ] Prompt tested with sample queries

## Interface Layer Implementation
- [ ] UI/API scaffolding complete
- [ ] Core user flow working
- [ ] Authentication implemented
- [ ] Access control implemented
- [ ] Error handling in place
- [ ] Loading states handled
- [ ] Responsive/accessible (if UI)

## Guardrails Implementation
- [ ] Read-only enforcement (if applicable)
- [ ] Bounded query enforcement
- [ ] Rate limiting
- [ ] Input validation
- [ ] Output sanitization
- [ ] Audit logging

## Testing

### Unit Tests
- [ ] Data layer functions tested
- [ ] Core logic tested
- [ ] Guardrails tested

### Integration Tests
- [ ] End-to-end flow tested
- [ ] API integrations verified
- [ ] Error scenarios tested

### User Acceptance Testing
- [ ] Real queries tested
- [ ] Real users involved
- [ ] Edge cases tested
- [ ] Feedback collected

### Regression Tests
- [ ] Test cases documented
- [ ] Automated where possible
- [ ] Baseline established

## Deployment

### Pre-Deploy
- [ ] All tests passing
- [ ] Code reviewed
- [ ] Environment variables set
- [ ] Secrets configured
- [ ] Monitoring ready

### Deploy
- [ ] Staging deployment successful
- [ ] Staging tested
- [ ] Production deployment successful
- [ ] Production smoke tests pass

### Post-Deploy
- [ ] Health checks passing
- [ ] Monitoring confirmed working
- [ ] Logging confirmed working
- [ ] Rollback tested (or plan verified)

## Documentation
- [ ] CORTEX.md finalized
- [ ] User guide created (if needed)
- [ ] Technical documentation updated
- [ ] Known issues documented

## Handoff
- [ ] Client trained on system
- [ ] Support process defined
- [ ] Feedback channel established
- [ ] Phase 5 (Iterate) kickoff scheduled

## Phase Exit Criteria
**Phase 4 is complete when ALL of the following are true:**
- [ ] Data Layer is ingesting and transforming correctly
- [ ] Cortex is complete with all Domain Spec rules encoded
- [ ] Interface is functional and tested
- [ ] Guardrails are preventing bad outputs
- [ ] Real users have tested with real questions
- [ ] System is deployed to production
- [ ] Monitoring and logging are operational
- [ ] Client has been trained
- [ ] Iteration process is defined
