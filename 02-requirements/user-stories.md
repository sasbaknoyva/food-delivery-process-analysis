# Requirements: User Stories

Each story is linked to a business goal from [business-case.md](../01-business-case/business-case.md):
G1 = delivery time, G2 = cancellation rate, G3 = customer rating.

## Customer

**US-01 Delivery time estimate** (G1, G3)
As a customer, I want to see an accurate estimated delivery time before I order, so that I can decide whether to place the order.
- ETA is shown on the checkout screen
- ETA is based on restaurant preparation time and courier distance
- ETA is updated if a peak-hour delay of more than 10 minutes is expected

**US-02 Order tracking** (G3)
As a customer, I want to track my order status in real time, so that I know when it will arrive.
- Statuses: Placed, Confirmed, Preparing, Picked up, Delivered
- A push notification is sent on every status change
- Courier location is visible on the map after pickup

**US-03 Order cancellation** (G2)
As a customer, I want to cancel an order before it is prepared, so that I do not pay for food I no longer need.
- Free cancellation is possible until the restaurant confirms the order
- After confirmation, a cancellation reason is required
- Refund status is shown in the app

**US-04 Problem reporting** (G3)
As a customer, I want to report a missing or wrong item in the app, so that my problem is solved quickly.
- Report is possible within 30 minutes after delivery
- Customer can attach a photo
- Support replies within 15 minutes

## Restaurant

**US-05 Order confirmation** (G2)
As a restaurant, I want to receive a clear new-order alert with a confirmation timer, so that I do not miss orders.
- Alert is shown with sound and notification
- Restaurant accepts or rejects within 3 minutes
- If there is no response, the customer is notified and the order is cancelled automatically

**US-06 Menu availability** (G2)
As a restaurant, I want to mark items as unavailable, so that customers cannot order items we do not have.
- Unavailable items disappear from the menu immediately
- Restaurant can mark them available again at any time

**US-07 Preparation time** (G1)
As a restaurant, I want to set the preparation time for each order, so that couriers arrive when the food is ready.
- Default preparation time is set per restaurant
- Time can be adjusted when confirming an order

**US-08 Ready for pickup** (G1)
As a restaurant, I want to mark an order as ready, so that the courier is notified immediately.
- Courier receives a notification when status changes to Ready
- Ready time is recorded for analysis

## Courier

**US-09 Order assignment** (G1)
As a courier, I want to receive orders close to my location, so that I spend less time on the road.
- Order is offered to the nearest available courier
- Courier accepts within 60 seconds, otherwise the order is offered to the next courier
- Pickup address, drop-off address and estimated earnings are shown

**US-10 Navigation and order details** (G1)
As a courier, I want to see the route and order details in one screen, so that I do not need extra apps.
- Route to restaurant and to customer is shown
- Customer phone number is masked

**US-11 Pickup and delivery confirmation** (G3)
As a courier, I want to confirm pickup and delivery in the app, so that the order status is always correct.
- Item checklist is shown at pickup
- Pickup and delivery are recorded with a timestamp

## Operations

**US-12 KPI dashboard** (G1, G2)
As an operations manager, I want to see live KPIs, so that I can react to problems quickly.
- Average delivery time, cancellation rate, active orders and courier utilization are shown
- Data can be filtered by hour and district
- Dashboard refreshes every 5 minutes

**US-13 Delay alerts** (G1)
As an operations manager, I want to be alerted when an order is delayed, so that I can reassign it.
- Alert is triggered when delivery exceeds ETA by 10 minutes
- Manager can reassign the order to another courier

## Non-Functional Requirements
| ID | Requirement |
|---|---|
| NFR-01 | ETA calculation responds in under 2 seconds |
| NFR-02 | Platform availability of at least 99.5% |
| NFR-03 | Personal data (phone, address) is visible only to the assigned courier during delivery |
| NFR-04 | Apps support Azerbaijani and English |