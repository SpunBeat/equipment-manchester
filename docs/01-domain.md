# System Domain

## Main Entities
- User (or Customer)
- Equipment
- Rental Contract
- Assignment
- Payment
- Incident

## Key Relationships
- Equipment can be assigned to an active contract
- A contract has one or more payments
- A user can have multiple contracts

## Critical States
### Equipment
- Available
- Rented
- Under Maintenance
- Out of Service

### Contract
- Draft
- Active
- Overdue
- Closed