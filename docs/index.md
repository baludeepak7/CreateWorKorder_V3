**CreateWorkOrder_V3**

Service Description
===================

*The CreateWorkOrder V3 is part of the integration flow “Work Order
Tracking & Management”.This is a technical service for creating a cable
work order in ICOMS. Accepts all the required fields from the consumer
and invokes the ICOMS Macro for creating a work order. Sends an Error or
successful response back to consumer.*

The service in addition to an appointment associated with the work
order, can additionally accept third party installation appointment (for
example: faceplate installation).

*Appointments are distinguished using callCode in the appointment. If
callCode is not available, it will be considered by default to be
associated with work order and not that of a third party installation.
Service performs no validation on appointments. For example if multiple
appointments of same callCode or no callCodes are passed, it picks the
first one in the list.*[[]{#_Toc256000916
.anchor}]{#scroll-bookmark-2064 .anchor}

### CreateWorkOrder

### Request 

  **Header Name**        **Type**
  ---------------------- --------------------
  Activity Name          string
  msgType                RequestMessageType
  senderURI              string
  OriginatorURI          string
  replyToURI             string
  failureToURI           string
  Userid                 string
  security               string
  securityType           string
  RequestTimestamp       dateTime
  CommunicationPattern   string
  CommunicationStyle     string
  Service                string
  Version                string
  BusinessID             string
  ConversationID         string
  RequestID              string
  MessageID              string

### Response

**Parameter**                        **Description**
  ------------------------------------ ----------------------------------------------------------------------------------------------------------------------
  orderNumber                          A number that uniquely identifies a CustomerOrder within the ordering Customer’s enterprise. Example Value:104118503
  ProratedAmount.amount                The quantity of money (positive or negative) represented as floating point number.
  ProratedAmount.currency              Currency generally accepted form of money.
  changeAmount.amount                  The quantity of money (positive or negative) represented as floating point number.
  changeAmount.currency                Currency generally accepted form of money.
  monthlyAmount.amount                 The quantity of money (positive or negative) represented as floating point number.
  monthlyAmount.currency               Currency generally accepted form of money.
  totalOneOffCharge.amount             The quantity of money (positive or negative) represented as floating point number.
  totalOneOffCharge.currency           Currency generally accepted form of money.
  totalMonthlyServiceAmount.amount     The quantity of money (positive or negative) represented as floating point number.
  totalMonthlyServiceAmount.currency   Currency generally accepted form of money.
  Campaign.amount                      The quantity of money (positive or negative) represented as floating point number.
  campaign.currency                    Currency generally accepted form of money.
  postCampaignAmount.amount            The quantity of money (positive or negative) represented as floating point number.
  postCampaignAmount.currency          Currency generally accepted form of money.
  installAmount.amount                 The quantity of money (positive or negative) represented as floating point number.
  installAmount.currency               Currency generally accepted form of money.
  workOrderPoints                      Number of work order points to fullfill the workorder

  Error response
--------------

  **Type**   **Code**   **Description**            **Severity**   **Source System**
  ---------- ---------- -------------------------- -------------- -------------------
  SYSTEM     2020       Unexpected Error           CRITICAL       SERVICE
  BUSINESS   10007      Schema Validation Error    CRITICAL       SERVICE
  BUSINESS   10465      ICOMS Business Exception   CRITICAL       SERVICE
  SYSTEM     10466      ICOMS System Exception     CRITICAL       SERVICE

