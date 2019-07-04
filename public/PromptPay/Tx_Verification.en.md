3.1 Transaction Verification

3.1.1 Description

Creditor bank (Receiving Bank) can verify payment transaction using unique reference from Debtor Bank (Sending Bank) where Bank account already been deducted from Debtor bank customer.

This API can rectify on the problem where customer already paid or transfer money to Creditor bank but money does not been added to Creditor bank customer, Creditor bank customer can verify and ensure that he/she will receive money from customer definitely.

3.1.2 Parameters

HTTP Method GET

Resource Path /prompay/transactions?sendingBank={sendingBank}&transref={transRef}

Produces application/json

3.1.3 Request Parameter

3.1.3.1 HEADER PARAMETERS

Header Name Description

Partner-Id Partner ID ที่ได้รับจาก KBank

Partner-Secret Partner Secret ที่ได้รับจาก KBank

3.1.3.2 URL PARAMETERS

Field Name Type Mandatory Description

sendingBank string(3) M Sending bank

transRef string(25) M Def(En): Transaction Reference Number Contains Reference number of the transaction required t