# Knowledge Capturer Project
## Exercise 1 
## Glossary
**3DS (3 Domain Structure)**

This is a security protocol that helps prevent fraud in online credit and debit card transactions. It involves three players namely the issuer, the acquirer, and the interoperability domain.

**AML (Anti Money Laundering)**

Laws and regulations intended to prevent criminals from illegally obtained funds as legitimate income.

**ATM (Automated Teller Machine)**

An ATM is an interactive terminal with a touch screen or keypad allowing consumers with debit or credit cards to withdraw cash and make deposits using a magnetically encoded card. 

**BIN (Bank Identification Number)**

BIN refers to the first four to six digits on a payment card. These numbers identify the financial institutions that issue the card. 

**CR (Credit)**

This is an accounting entry that either decreases assets or increases liabilities on a balance sheet.

**CVC (Card Verification Code)**

This is a three or four digit code found on debit and credit cards and is used as a number checking system against fraud protection. 

**CVV (Card Verification Value)**

This is a number found at either the back or front of debit cards and is used for completing online transactions.

**DR (Debit)**

This is an accounting entry resulting in either an increase in assets or a decrease in liabilities on a balance sheet.

**EFT (Electronic Funds Transfer)**

This is an electronically based system of transferring funds to and from accounts. 

**EMV (Europay, MasterCard and Visa)**

This is a payment technology standard for debit and credit card transactions providing transaction security features and reduced risk of card-present fraud.

**HCE (Host Card Emulation)**

This is technology securing mobile phones so that they can be used to make credit or debit transactions at physical point-of-sale terminals. 

**KYC (Know Your Customer)**

This is the process of verifying a customer’s identity so as to prevent financial institutions from being used by criminals to launder money. 

**MCC (Merchant Category Codes)**

These are four-digit numbers that credit issuers use to classify transactions consumers complete using a particular card.

**MDES (MasterCard Digital Enablement Service)**

This is a platform which allows users to use any device with internet connectivity for commission and payments acceptance.

**PAN (Primary Account Number)**

This refers to a 14-19 digit number generated as a unique identifier designated for a primary account.

**PCI (Payment Card Industry)**

The PCI is the sector of the financial industry that regulates the use of all electronic forms of payment.

**PIN (Personal Identification Number)**

This is a numerical code usually issues in association with payment cards to make EFT transactions. The card ensures there is an additional layer of security for electronic transactions.

**POS (Point of Sale)**

A POS is the location in a business premises where a sale that is transacted by payment for goods or services is received.

## Exercise 2
## Knowledge Based Article
### Table of Contents
- [What is EMV 3DS](#what-is-emv-3ds)
- [Static versus Dynamic One Time Passwords](#static-versus-dynamic-one-time-passwords)
- [How does 3DS2 work](#how-does-3ds2-work)
- [What is the Impact of the 3DS2 changes on our clients](#what-is-the-impact-of-the-3ds2-changes-on-our-clients)
- [How do we manage the risk](#how-do-we-manage-the-risk)
- [Glossary](#glossary)


### What is EMV 3DS?
EMV Three-Domain Secure (3DS) is a messaging protocol developed by [EMVCo](https://www.emvco.com/) to enable consumer authentication during card-not-present (CNP) e-commerce purchases.

It is a fraud prevention tool that adds an additional security layer when the cardholder makes card-not-present (CNP) e-commerce purchases by enabling cardholder authentication, often in a frictionless way by consuming payment history and richer data that reliably indicates the purchaser is the owner of the card details. Frictionless authentication means the cardholder does not require to use a One Time Password (OTP).

In recent years, 3DS has evolved from the initial version, known as 3DS1 to a later and more secure version 3DS2.

### Static versus Dynamic  One Time Passwords 
Static passwords apply to 3DS1 **only** and hence our clients have slowly migrated from using static passwords onto Dynamic 3DS passwords. In this instance, the cardholder is sent a unique OTP on each login attempt rather than using static security questions or passwords. This move is a pre-requisite for 3DS2.
### How does 3DS2 work? 
The 3DS transaction approval process consists of two phases:

•    Authentication – Validates the cardholder before moving onto the next phase of the process.

•	Authorization – Considers the outcome of the authentication step before checking business as usual authorization criteria. This includes the availability of funds and approving or declining the transaction.

The Authentication step is performed by ACS (Bankserve) or in some instances by  
[Mastercard](https://www.mastercard.com/global/en.html) Stand-In processing. The outcome of the Authentication process is sent to the Issuer in the Authorization message to consume during the Authorization process. The following Data Elements are key for the Issuer to make the final Authorization decision:

•    DE48 SE42 (Security Level Indicator - SLI)

•    DE48 SE43 Leading Indicator

**Fully authenticated transactions**

During the ACS (Bankserve) authentication process, an Issuer Authentication Value (IAV) is generated and included in the Accountholder Authentication Value (AAV).

A transaction that was **fully authenticated** by ACS will have an IAV which must be validated by the Issuer during the authorization process. This validation consists of the PAN and Transaction ID and the Issuer extracts the IAV from bytes 3-6 of the AAV.

Fully authenticated transactions can be identified by a Security Level Indicator (SLI) of 212 in DE48 SE42. The SLI work hand-in-hand with a Leading Indicator in DE48 SE 43 that indicates the type of transaction.

In some instances, [Mastercard](https://www.mastercard.com/global/en.html) Smart Authentication will use risk-based decision making to fully authenticate transactions. These will not go through the ACS and will therefore not have an IAV to validate, only [Mastercard](https://www.mastercard.com/global/en.html) can validate the AAV in these instances. These transactions can be identified by the Leading Indicator kC in DE48 SE43 and will still be fully authenticated by [Mastercard](https://www.mastercard.com/global/en.html) with an SLI 212.

In [Paymentology](https://www.paymentology.com/) fully authenticated transactions where the IAV is successfully validated, transactions are processed as ‘Approved’ during the authorization process. This is as long as all other Authorization checks are met. An example of this is availability of funds.

In 3DS, the liability of the transaction in case of fraud shifts from the merchant to the issuer in most instances. However, the transaction liability can remain with the merchant provided all other authorization
checks such as checking for availability of funds are met.

All other transactions that are not fully authenticated will follow a decision path that considers Fraud and Security Data provided by [Mastercard](https://www.mastercard.com/global/en.html) in the authorization message, if the specific BIN is enrolled in Decision Intelligence.

Decision Intelligence is a service provided by [Mastercard](https://www.mastercard.com/global/en.html) in which the issuing client must pay for. At the moment, not all the clients have enrolled in this service. This makes the decision making process more challenging and riskier. There are [Mastercard](https://www.mastercard.com/global/en.html) imposed Data Integrity Edits that limit the number of transactions that may be declined. It therefore becomes a fine balance between approving transactions and declining where there is no Fraud and Security data.

If available, the following Data Elements are considered during the authorization process : 

•	DE48 SE71 On Behalf Service 06

•	DE48 SE75 Fraud Scoring Data

•	DE48 SE56 Security Services for Issuers (AIQ; ARA)
### What is the Impact of the 3DS2 changes on our clients? 
[Paymentology](https://www.paymentology.com/) clients that are currently on 3DS1 must enroll in [Mastercard](https://www.mastercard.com/global/en.html) Identity Check for BINS to be 3DS2 enabled.  Transactions are processed under the 3DS2 protocol provided the merchant is also 3DS2 enabled. If not, the transaction will still be processed as a 3DS1 transaction, regardless of it being a 3DS2 enabled Issuer BIN.

For this reason, [Paymentology](https://www.paymentology.com/)  must be able to process both 3DS1 and 3DS2 transactions until all 3DS1 processing is decommissioned by [Mastercard](https://www.mastercard.com/global/en.html)  across the 3DS eco-system on 14 October 2022.
### How do we manage the risk? 

In instances where there is no Fraud and Security data to consider, there is a fine balance between approving and declining transactions. Issuing clients must enroll in Decision Intelligence to receive this information.


If these edits are failed, then fees will be imposed on the client. For this reason, monitoring on an on-going basis is required to evaluate the impact of the decision making path on the specific client’s transactions.

Reports are available to undertake this monitoring on behalf of clients. It is particularly important to do so for new clients to ensure our decision making logic is sound. In addition, it is key to evaluate the risk in case high risk transactions are approved that may lead to Chargeback exposure where the Issuer is liable for Fraud related Chargebacks.

**Note**: Fraud Chargebacks may not be submitted on transactions where the liability shift is on the Issuer. The reports can be accessed through the Voucher Engine, under Admin Reports.

### Glossary 
**3DS1**

This is an XML protocol, integrating an additional security layer for online credit card transactions.

**3DS2**

 This is an enhanced consumer experience system supporting transmission of rich data during transactions which aids in risk based decisions.

**Accountholder Authentication Value (AAV)** 

 This is a security code issued as part of Mastercards secure payment application to third party credit card verification vendors.

**BINS**

 Refers to the first four to six digits on a payment card. These numbers identify the financial institutions that issue the card.

**Data Integrity Edits (DIE)** 

 These are edits done ensuring maintenance and assurance of data accuracy and consistency over its entire life cycle.

**Dynamic Passwords**

 Passwords that constantly change and do not remain the same.

**EMVCo**

 This is a global body that facilitates the worldwide interoperability and acceptance of secure payment transactions by managing and evolving the EMV® Specifications and related testing processes.

**Issuer Authentication Value (IAV)** 

 An authentication code in which Issuers can perform self validation for themselves.

**Primary Account Number (PAN)** 

 This refers to a 14-19 digit number generated as a unique identifier designated for a primary account.

**Security Level Indicator (SLI)**

 Defines anything out of the ordinary which may be a threat to security.

**Static Passwords**

 Passwords that remain the same unless deliberately changed or reset by an end-user or administrator.
## Exercise 3

### Actions to perform when a Vodacom Voucher Expires 

If a task fails, it will throw either one or more errors, each with its own tracking number. 
#### Possible Error Messages

•	Load wallet call failed.  

•	Devalue failed but wallet was loaded.

•	Retire failed, but wallet was loaded and card was devalued.

If a voucher expires holding a positive balance, the *devalueExpiredVodacom* task performs three functions;
1. Load the customer's wallet using the B2CBroker- If the process fails at this stage, re-run the task.
2. Devalue the voucher- If the process fails at this stage;

    i) Open the voucherengine.tutuka.com/check/vodacomscript script and modify it. 

    ii) Run the modified voucherengine.tutuka.com/check/Vodacom script from SCH-01.

    iii) Add all voucher tracking numbers that failed with **"Devalue failed"** to the first array as shown below;


```
<cfscript>
// list of tracking numbers of vouchers that failed at devalue step (so they need to be devalued + retired)
failedDevalueVouchers = []; 
```
3.  Retire the voucher- If the process fails at this stage; add the tracking numbers for those vouchers to the second array as shown below. 
```
<cfscript>
// list of tracking numbers of vouchers that failed at retire step (they only need to be retired)
failedRetireVouchers = [];
```

4. Run the script from your browser once all the vouchers have been added. This should devalue and retire all the vouchers. 

    **Note**: If this process fails, then further investigation will need to be conducted.


