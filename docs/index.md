CreateWorkOrder\_V3

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

  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  **Parameter**                                                          **Description**
  ---------------------------------------------------------------------- ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  CreateWorkOrderRequest.accountIdentification.accountNumer              A unique service account identifier may only be unique with the combination of service address and site Reference, Account number is a unique identifier representing the customer account. Example Value:104118503

  CreateWorkOrderRequest.accountIdentification.siteReference             A unique service account identifier may only be unique with the combination of accountNumber and site Reference, Site Reference can be used to describe system andor system instance identifier. Example Value:26

  CreateWorkOrderRequest.workOrderHeader.callCode                        Call Code representing work order type.\
                                                                         Example Value: 1,1

  CreateWorkOrderRequest.workOrderHeader.workOrderTaskCode               Task codes are used to signify whether it as a new install of a change service and whether it is office only or not.\
                                                                         Example: INSTALLOFFN

  CreateWorkOrderRequest.workOrderHeader.assignedInstaller               Assigned installer for the work order.\
                                                                         Example: 34456

  CreateWorkOrderRequest.workOrderHeader.campaignCode                    Campaign Code.

  CreateWorkOrderRequest.workOrderHeader.salesRepresentativeIdentifier   Sales Representative Identifier\
                                                                         Example: 85489

  CreateWorkOrderRequest.workOrderHeader.salesReasonCode                 Reason number as specified by the sales representative in-order that a sales(customer) order has been rescheduled.

  CreateWorkOrderRequest.workOrderHeader.salesTypeCode                   Represents employee type code in order to achieve an sales work order.\
                                                                         Typical value: “03”

  CreateWorkOrderRequest.workOrderHeader.orderStatusCode                 Work Order status code.\
                                                                         Example Value: FB

  CreateWorkOrderRequest.workOrderHeader.orderComment                    Customer comments for the order. It is created as part of work order creation with maximum length of 40. The text will need to be split up into multiple comment lines and only in upper case.

  CreateWorkOrderRequest.workOrderHeader.billStartDate                   Bill Start Date.

  CreateWorkOrderRequest.workOrderHeader.primaryFindingCode              Primary Finding Code.

  CreateWorkOrderRequest.workOrderHeader.primarySolutionCode             Primary Solution Code.

  CreateWorkOrderRequest.workOrderHeader.retainWorkOrder                 This flag is used to set commit on an workorder request.

  CreateWorkOrderRequest.workOrderHeader.is30DayWorkOrder                Flag to indicate if work order being created is a 30 day work order request

  CreateWorkOrderRequest.workOrderHeader.prorateWorkOrder                Flag to indicate if work order being created is a prorate work order request

  CreateWorkOrderRequest.workOrderHeader.consumerReference               Order identifier given to the order by the consumer.

  CreateWorkOrderRequest.serviceCategory                                 

  CreateWorkOrderRequest.appointment                                     

  CreateWorkOrderRequest.oneTimeService                                  

  CreateWorkOrderRequest.Questionnaire                                   

  CreateWorkOrderRequest.telephoneServiceSwap                            

  CreateWorkOrderRequest.CSSDetails                                      
  --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

### Response {#response .ListParagraph}

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
