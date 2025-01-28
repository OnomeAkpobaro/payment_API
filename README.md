# Django Payment API

A robust Django REST API for handling payment operations with Paystack integration. This API provides comprehensive payment processing capabilities including payment initialization, verification, refunds, and payment history tracking.

## Features

- Payment processing with Paystack integration
- Payment history tracking
- Refund management
- Additional charges handling with tax calculations
- Webhook support for payment status updates
- Comprehensive payment lifecycle management
- Secure payment verification
- Detailed transaction logging

## Prerequisites

- Python 3.8+
- Django 5.1.4+
- Django REST Framework
- Paystack account with API keys

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd payment_API
```

2. Create and activate a virtual environment:
```bash
python -m venv venv
source venv/bin/activate  # On Windows use: venv\Scripts\activate
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Configure environment variables:
   - Create a `.env` file in the project root
   - Add your Paystack credentials:
```
PAYSTACK_SECRET_KEY=your_secret_key
PAYSTACK_PUBLIC_KEY=your_public_key
```

5. Run migrations:
```bash
python manage.py migrate
```

6. Start the development server:
```bash
python manage.py runserver
```

## API Endpoints

### Payments
- `GET /api/v1/payments/` - List all payments
- `POST /api/v1/payments/` - Create a new payment
- `GET /api/v1/payments/{id}/` - Retrieve a specific payment
- `PUT /api/v1/payments/{id}/` - Update a payment
- `DELETE /api/v1/payments/{id}/` - Delete a payment
- `POST /api/v1/payments/{id}/process/` - Process a payment
- `POST /api/v1/payments/{id}/mark_failed/` - Mark a payment as failed
- `POST /api/v1/payments/{id}/initiate_payment/` - Initialize Paystack payment
- `POST /api/v1/payments/{id}/verify_payment/` - Verify Paystack payment

### Payment History
- `GET /api/v1/payment-history/` - List payment history
- `POST /api/v1/payment-history/` - Create payment history entry
- `POST /api/v1/payment-history/{id}/add_note/` - Add note to payment history

### Refunds
- `GET /api/v1/payment-refunds/` - List all refunds
- `POST /api/v1/payment-refunds/` - Create a refund
- `POST /api/v1/payment-refunds/{id}/process_refund/` - Process a refund

### Payment Charges
- `GET /api/v1/payment-charges/` - List all charges
- `POST /api/v1/payment-charges/` - Create a charge
- `GET /api/v1/payment-charges/{id}/calculate_total/` - Calculate total with tax

### Webhook
- `POST /api/v1/webhook/paystack/` - Paystack webhook endpoint



POSTMAN TEST:

- `POST: https://od1212.pythonanywhere.com/api/v1/payments/

{
    "amount": "This field is required.",
    "customer_name": "This field is required.",
    "email": "This field is required."

}

- `POST: https://od1212.pythonanywhere.com/api/v1/payments/1/initiate_payment/

*change transaction_id to current transaction_id*
This generates the paystack link for payment.


- `GET: https://od1212.pythonanywhere.com/api/v1/payments/1/

*change transaction_id to current transaction_id*
This retrieves the status of the specific payment



## Models

### Payment
The main payment model handling basic payment information:
- Transaction ID
- Customer Name
- Amount
- Email
- Status (PENDING/COMPLETED/FAILED)
- Payment Reference
- Created/Updated timestamps

### PaymentHistory
Tracks the history of payments:
- Links to original payment
- Notes
- Status tracking
- Timestamps

### PaymentRefund
Handles refund operations:
- Original payment reference
- Refund reason
- Refund amount
- Status tracking

### PaymentCharge
Manages additional charges:
- Base amount
- Tax amount
- Total calculation
- Description

## Error Handling

The API includes comprehensive error handling:
- Custom PaymentOperationError
- Validation errors for payment amounts
- Email format validation
- Duplicate transaction prevention
- Webhook signature verification

## Security Features

- CSRF protection enabled
- Authentication middleware
- Secure webhook verification
- Payment amount validation
- Duplicate transaction prevention
- Paystack signature verification

## Testing

Run the test suite:
```bash
python manage.py test
```

## CI/CD

The project includes GitHub Actions workflow for:
- Running tests
- Checking Python syntax
- Verifying dependencies

## Contributing

1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request













