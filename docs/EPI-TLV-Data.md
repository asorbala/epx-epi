# TLV Data

### TLV overview
EPX requires Money Transfer (Visa) and MoneySend (MasterCard) data to be presented in taglength-value (TLV) format, which is a method of encoding information in a single string, versus multiple EPX tags.

### TLV_SETS tag
Each request must contain the tag TLV_SETS. This tag can contain multiple TLV sets, which are concatenated together. The maximum length for the TLV_SETS value is 4000 bytes.
A logical simplification for the TLV_SETS tag is as follows (with spaces added for readability):

`TLV_SETS = "set_length TLVset . . . set_length TLVsetN"`

Where:
- **set_length** is the 4-digit byte count for the length of the referenced TLV set. For example, if a TLV set contains two TLV elements with lengths of 25 and 30, the TLV set length is `0055`.
- **TLVset** is the set of TLV elements. A TLV set will contain at least two TLV elements. The TLV elements can be presented in any order within a set.

**Note**: *For MoneySend Payment and Funding transactions, the TLV_SETS tag must always
include a “RECEIVER” and “SENDER” TLV set, in addition to any other desired TLV set.*

### TLV elements
As previously described, a TLV set consists of two or more TLV elements. A TLV element itself
consists of three sub-elements:
- Tag: A 3-digit tag number such as 012 or 000 to describe the type of data. The tag has
significance within the context of its parent TLV set. Thus, a tag 001 in a TRAN_DATA TLV
set has a different meaning than 001 in a RECEIVER TLV set.
- Length: A 3-digit number representing the byte count for the value associated with the
element
- Value: A variable alpha-numeric field
For example, the TLV element 003005Jones in the TLV set “SENDER” is parsed as follows:
Public - Security Level 0
API – EPX Payment Interface 14 of 28
- 003: Identifies the element as a Last Name object
- 005: Specifies that the length that follows (Jones) is 5 bytes
- Jones: Provides the value for Last Name

### EPX TLV Elements for Money Transfer (Visa) and MoneySend (MasterCard) Funding / Payment

Tables below provide the mandatory and optional tags to include with Visa Funding (AFT) / MasterCard MoneySend and Payment (OCT) TLV fields.
The CARD_ID should be included in the transaction request to identify whether the cardholder is present.

NOTE: *TLV elements can be presented in any order within a TLV set.*

### Identification Type Codes - MasterCard
Below table provides values for the Identification Type Codes for use with the "RECEIVER", and "SENDER" TLV sets for MasterCard transactions.

Table 5: Identification Type Code values - MasterCard

|Value| Definition|
|---|---|
|01| Passport|
|02| National Identification Card|
|03| Driver’s License|
|04|Government Issued|
|05| Other|

### TLV set – "RECEIVER"
NOTE: *The RECEIVER TLV set is mandatory for all Money Transfer Payment and Funding
transactions.*

Table 6: TLV tag properties for TLV set “RECEIVER” - Visa

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “RECEIVER”|8| Alpha| Mandatory| Mandatory|

Table 7: TLV tag properties for TLV set “RECEIVER” - MasterCard

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “RECEIVER”|8| Alpha| Mandatory| Mandatory|
|001| First Name| 35| Alphanumeric| Optional| Conditional|
|002| Middle Name| 1| Alphanumeric| Optional| Optional|
|003| Last Name| 35| Alphanumeric| Optional| Conditional|
|004| Street Address| 50| Alphanumeric| Optional| Optional|
|005| City| 25| Alphanumeric| Optional| Optional|
|006 |State/Province Code|3| Alphanumeric| Optional| Optional|
|007| Country| 3| Alphanumeric| Optional| Optional|
|008| Zip/Postal Code| 10| Alphanumeric| Optional| Optional|
|009| Phone Number| 20| Numeric| Optional| Optional|
|010| Date of Birth| 8| Numeric| Optional| Optional|
|011| Account Number| 20| Numeric| Optional| Optional|
|013| Identification Type <br>Examples:<br>01 = Passport<br>03 = Government Issued|2| Numeric| Optional| Optional|
|014| Identification Number|25| Alphanumeric| Optional| Optional|
|015| Identification Country Code|3| Alphanumeric| Optional| Optional|
|016| Identification Expiration Data| 8| Numeric| Optional| Optional|
|017| Nationality| 3| Alphanumeric| Optional| Optional|
|018| Country of Birth| 3| Alphanumeric| Optional| Optional|

### TLV set – “SENDER”
NOTE: *The SENDER TLV set is mandatory for all Money Transfer Payment and Funding
transactions.*

Table 8: TLV tag properties for TLV set "SENDER" - Visa

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “SENDER” |6| Alpha| Mandatory| Mandatory|
|001| First Name| 30| Alphanumeric| Optional| Optional|
|002| Middle Name| 1| Alphanumeric| Optional| Optional|
|003| Last Name|30|Alphanumeric| Optional |Mandatory|
|004| Street Address| 35| Alphanumeric| Optional| Mandatory|
|005| City| 25| Alphanumeric| Optional| Mandatory|
|006| State/Province Code|2| Alphanumeric| Optional| Mandatory|
|007| Country ISO code|3| Alphanumeric| Optional| Mandatory|
|011| Account Number| 34| Alphanumeric| Optional| Mandatory|
|012| Reference Number| 16| Alphanumeric| Optional| Mandatory|

Table 9: TLV tag properties for TLV set "SENDER" - MasterCard

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value "SENDER"|8| Alpha| Mandatory| Mandatory|
|001| First Name| 35| Alphanumeric| Optional| Conditional|
|002| Middle Name| 1| Alphanumeric| Optional| Optional|
|003| Last Name| 35| Alphanumeric| Optional| Conditional|
|004| Street Address| 50| Alphanumeric| Optional| Optional|
|005| City| 25| Alphanumeric| Optional| Optional|
|006 |State/Province Code|3| Alphanumeric| Optional| Optional|
|007| Country| 3| Alphanumeric| Optional| Optional|
|008| Zip/Postal Code| 10| Alphanumeric| Optional| Optional|
|009| Phone Number| 20| Numeric| Optional| Optional|
|010| Date of Birth| 8| Numeric| Optional| Optional|
|011| Account Number| 20| Numeric| Optional| Optional|
|013| Identification Type <br>Examples:<br>01 = Passport<br>03 = Government Issued|2| Numeric| Optional| Optional|
|014| Identification Number|25| Alphanumeric| Optional| Optional|
|015| Identification Country Code|3| Alphanumeric| Optional| Optional|
|016| Identification Expiration Data| 8| Numeric| Optional| Optional|
|017| Nationality| 3| Alphanumeric| Optional| Optional|
|018| Country of Birth| 3| Alphanumeric| Optional| Optional|

### TLV set – “TRAN_DATA”

Table 10: TLV tag properties for TLV set “TRAN_DATA” - Visa

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “TRAN_DATA”| 9 |Alpha| Mandatory| Mandatory|
|001| Funding Source<br>Examples:<br>V1 = Visa Credit<br>V2 = Visa Debit|2|Alphanumeric| Optional| Mandatory|
|005| Business Application Identifier| 2| |Mandatory |Mandatory|

Table 11: TLV tag properties for TLV set “TRAN_DATA” - MasterCard

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “TRAN_DATA”| 9 |Alpha| Mandatory| Mandatory|
|001| Funding Source<br>Examples:<br>V1 = Visa Credit<br>V2 = Visa Debit|2|Alphanumeric| Optional| Mandatory|
|002| Additional Message|65| Alphanumeric| Optional| Optional|
|003| Participant ID| 30| Alphanumeric| Optional| Optional|
|004| Transaction Purpose<br>Examples:<br>01 = Family Support <br>03 =Travel&Tourism|2| Numeric| Optional| Optional|

### Transaction Purpose
Table 12 provides Transaction Purpose values for use with the “TRAN_DATA” TLV set.

Table 12: Transaction Purpose values - MasterCard

|Value| Definition|
|---|---|
|01 |Family Support|
|02| Regular Labor Transfers (expatriates)|
|03 |Travel & Tourism|
|04| Education|
|05| Hospitalization & Medical Treatment|
|06| Emergency Need|
|07| Savings|
|08| Gifts|
|09| Others|

### TLV set – “LANG_DATA”

Table 13: TLV tag properties for TLV set “LANG_DATA” - Visa

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “LANG_DATA”| 9| Alpha| Optional| Optional|

Table 14: TLV tag properties for TLV set “LANG_DATA” - MasterCard

|TLV Tag| TLV Data| TLV Max Length|Type| AFT (Funding)| OCT (Payment)|
|---|---|---|---|---|---|
|000| Always use the value “LANG_DATA”| 9| Alpha| Optional| Optional|
|001| Language Identification| 3 |Alphanumeric| Conditional| Conditional|
|002| Language Data| 100| Alphanumeric| Optional| Optional|

### Funding Source Codes
Table 15 provides values for the Funding Source Codes.
Table 15: Funding Source Code values - Visa


|Value| Definition|
|---|---|
|04| Cash|
|05| DDA Account|
|06| Mobile Money Account|
|V1| Visa Credit|
|V2| Visa Debit|
|V3| Visa Prepaid|

Table 16: Funding Source Code values - MasterCard

|Value| Definition|
|---|---|
|01| Credit (Non Visa)|
|02| Debit (Non Visa)|
|03| Prepaid (Non Visa)|
|04| Cash|
|05| DDA Account|
|06| Mobile Money Account|

### Business Application Identifiers
Table 17 provides applicable OCT values for the Business Application Identifiers.
Table 17: Applicable OCT Business Application Identifier values - Visa

|Value| Definition|
|---|---|
|AA| Account to Account / Sender and Recipient are the same person|
|BA| I Value Description|
|BB| Business to Business|
|BI| Money transfer—bank-initiated|
|BP| Non-card bill payment|
|CP| Card bill payment*|
|FD| Funds disbursement*|
|GD| Government disbursement|
|GP| Gambling payout (other than online gambling)|
|LO| Loyalty and offers|
|MD| Merchant disbursement*|
|MI| Money transfer—merchant-initiated|
|OG| Online gambling payout|
|PD| Payroll/pension disbursement|
|PP| Person to Person / Sender and Recipient are not the same person|
|TU| Top-Up for enhanced prepaid loads*|
|WT| Wallet transfer (digital wallet)|

Note: *Additional business application identifiers may be supported by the EPX platform, please confirm with your relationship manager or integration specialist.*

Table 18 provides the applicable AFT values for the Business Application Identifiers.
Table 18: Applicable AFT Business Application Identifier values - Visa

|Value |Definition|
|---|---|
|AA| Account to Account / Sender and Recipient are the same person|
|BI| I Value Description|
|PP| Business to Business|
|TO| Money transfer—bank-initiated|
|WT| Non-card bill payment|

### Card ID
Table 19 provides Card ID values.
Table 19: Card ID values - Visa

|Card ID| Types| Definition|
|---|---|---|
|0| Funding / Payment| Cardholder Present|
|1| Funding / Payment |Cardholder Not Present|
|M| Funding / Payment| Cardholder Present (card not readable)|

### TLV set – “NETWORK”
NOTE: *The NETWORK TLV set is reserved for internal MasterCard use to request additional
network response elements.*

If the NETWORK TLV set is included in the request, the response will contain:
- The System Trace Audit Number (STAN), if a value of “Y” is included with TLV tag 001 in
the request. A STAN response is a maximum of 6 bytes, alphanumeric.
- The Retrieval Reference Number (RRN), if a value of “Y” is included with TLV tag 002 in
the request. A RRN response is a maximum of 12 bytes, alphanumeric.

Table 20: TLV element properties for TLV set “NETWORK” - MasterCard

|TLV Tag| TLV Data| TLV Max Length| Type |Funding| Payment|
|---|---|---|---|---|---|
|000| Always use the value “NETWORK”| 7 |Alpha| Mandatory| Mandatory|
|001| STAN (System Trace Audit Number) Always set to “Y” to receive a response |1 |Alphanumeric| Optional| Optional|
|002| RRN (Retrieval Reference Number) Always set to “Y” to receive a response |1 |Alphanumeric| Optional| Optional|

### EPX TLV Elements for Hospitality Funding / Payment

Note: *In the table below, “M” represents Mandatory and “O” represents Optional*

Table 21: TLV Elements for Hospitality Funding / Payment

|TLV Tag| TLV Data| TLV Max Data| AMEX| Discover| MC| Visa|
|---|---|---|---|---|---|---|
|000| DATA_SET= LODGING| a-8||M|||
|001| Promotional Code||| O|||
|002| Additional Coupon||| O|||
|003| Corporate Client Code||| O|||
|004| Room Location||| O|||
|005| Bed Type||| O|||
|006| Room Type||| O|||
|007| Smoking Preference||| O|||
|008| Number of Rooms Booked||| O|||
|009| Number of Adults||| O|||
|010| Tax Elements||| O|||
|011| No Show Indicator| A-1 {Y,N}|| O| O||
|012| Rate Type||| O|||
|013| Travel Agency Code||| O|||
|014| Extra Charges| n ##.##|| O|||
|015| Travel Agency Name||| O| MI||
|016| Toll Free Number| an..16|| O| O||
|017| Number of Room Nights||| O| O||
|018| Arrival Date| n-8 (MMDDYYYY)||O| MI| MI|
|019| Departure Date| n-8 (MMDDYYYY)|| O| MI||
|020| Folio Number| an..25|| O| MI| MI|
|021| Facility Phone Number||| O| MI||
|022| Adjustment Amount||| O|||
|023| Room Rate||| O| O||
|024| Room Tax||| O| O||
|025| Program Code||| O| O||
|026| Phone Charges||| O| O||
|027| Room Service Charges||| O| O||
|028| Mini-Bar Charges||| O| O||
|029| Laundry Charges||| O| O||
|030| Other Charges| an..3|| O| O||
|031| Other Indicator||| O|||
|032| Gift Shop Charges||| O| O||
|033| Prepaid Amount||| O| O||
|034| Movie Charges||| O| O||
|035| Health Club Charges||| O| O||
|036| Valet Parking Charges||| O| O||
|037| Cash Disbursement||| O| O||
|038| Non-Room Charges||| O| O||
|039| Business Center Charges||| O| O||
|040| Remarks||| O|||
|041| Transaction Description|||| M||
|042| Custom Identifier|||| O||
|043| Carrier Code|||| O||
|044| Flight Number|||| O||
|045| Total Charges|||| O||
|046| Total Amount Charged on Credit Card||||O||
|047| Lounge/Bar Charges|||| O||
|048| Transportation Charges|||| O||
|049| Gratuity Charges|||| O||
|050| Conference Room Charges|||| O||
|051| Audio Visual Charges|||| O||
|052| Banquet Charges|||| O||
|053| Internet Access Charges|||| O||
|054| Early Departure Charges|||| O||
|055| Guest Name|||| O||
|056| Guest Number|||| O||
|057| Property Phone Number|||| O||
|058| Billing Adjustment|||| O||
|059| Restaurant Charges||| O| O||
|060| Other Services|||| O||
|061| Total Tax Amount|||| O||
|062| Total Tax Collected Indicator ||||O||
|063| Commodity Code||||O ||
|064| Detail Tax Amount 1|||| O||
|065| Detail Tax Amount 2 |||| O||
|066| Detail Tax Amount 3 |||| O||
|067| Detail Tax Amount 4 |||| O||
|068| Detail Tax Amount 5 |||| O||
|069| Detail Tax Amount 6 |||| O||
|070| Tax Exempt Indicator |||| O||
|071| Total Authorized Amount| SD-12||| O||
|072| Total Tax Amount |||| O||
|073| Total Non-Room Tax Amount |||| O||
|074| Fire Safety Act Indicator |||| O||

