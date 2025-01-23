PAYMENT_API

Payment_API for receiving payment from customers
Initiate_payment generates a paystack link that allows customers to make payments.


POSTMAN TEST:

POST: https://od1212.pythonanywhere.com/api/v1/payments/

{
    "amount": "This field is required.",
    "customer_name": "This field is required.",
    "email": "This field is required."

}

POST: https://od1212.pythonanywhere.com/api/v1/payments/1/initiate_payment/

*change transaction_id to current transaction_id*
This generates the paystack link for payment.


GET: https://od1212.pythonanywhere.com/api/v1/payments/1/

*change transaction_id to current transaction_id*
This retrieves the status of the specific payment


GET: https://od1212.pythonanywhere.com/api/v1/payment-history/

This retrieves list of payment history


POST: https://od1212.pythonanywhere.com/api/v1/payment-history/
This requests a certain payment history

GET: https://od1212.pythonanywhere.com/api/v1/payment-refunds/
This retireves list of payment refunds


POST: https://od1212.pythonanywhere.com/api/v1/payment-refunds/
This initiates a payment refund

GET: https://od1212.pythonanywhere.com/api/v1/payment-charges/
This retrieves payment charges for transactions


POST: https://od1212.pythonanywhere.com/api/v1/payment-charges/
This creates a charge (eg. Tax) for a payment.




