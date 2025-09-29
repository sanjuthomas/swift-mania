## MT103 vs pacs.008 
Aka: Single Customer Credit Transfer, FIToFICustomerCreditTransfer, Customer Payment, Payer to Payee.

| **MT103 Tag** | **Meaning** | **pacs.008 (ISO 20022 XML Element)** |
|---------------|-------------|---------------------------------------|
| `:20:` | Transaction Reference | `GrpHdr/MsgId` or `CdtTrfTxInf/PmtId/InstrId` |
| `:23B:` | Bank Operation Code | `CdtTrfTxInf/PmtTpInf/SvcLvl/Cd` |
| `:32A:` | Value Date, Currency, Amount | `CdtTrfTxInf/IntrBkSttlmDt` + `IntrBkSttlmAmt` |
| `:33B:` | Instructed Currency/Amount | `CdtTrfTxInf/InstdAmt` |
| `:36:` | Exchange Rate | `CdtTrfTxInf/XchgRate` |
| `:50A/K/F:` | Ordering Customer (Debtor) | `CdtTrfTxInf/Dbtr` + `DbtrAcct/Id` |
| `:52A/D:` | Ordering Institution (Debtor Agent) | `CdtTrfTxInf/DbtrAgt/FinInstnId` |
| `:53A/D:` | Sender’s Correspondent | `CdtTrfTxInf/InstgAgt/FinInstnId` *(usage varies)* |
| `:54A/D:` | Receiver’s Correspondent | `CdtTrfTxInf/InstdAgt/FinInstnId` or `IntrmyAgt` |
| `:56A/D:` | Intermediary Institution | `CdtTrfTxInf/IntrmyAgt1/FinInstnId` |
| `:57A/D:` | Creditor Agent (Beneficiary’s Bank) | `CdtTrfTxInf/CdtrAgt/FinInstnId` |
| `:59:` | Beneficiary Customer (Creditor) | `CdtTrfTxInf/Cdtr` + `CdtrAcct/Id` |
| `:70:` | Remittance Information | `CdtTrfTxInf/RmtInf/Ustrd` *(or `Strd`)* |
| `:71A:` | Charges (OUR/BEN/SHA) | `CdtTrfTxInf/ChrgBr` |
| `:71F:` | Sender’s Charges | `CdtTrfTxInf/ChrgsInf/Amt` |
| `:71G:` | Receiver’s Charges | `CdtTrfTxInf/ChrgsInf/Amt` *(depending on agent)* |
| `:72:` | Sender to Receiver Information | `CdtTrfTxInf/InstrForNxtAgt` / `InstrForCdtrAgt` |
| `:77B:` | Regulatory Reporting | `CdtTrfTxInf/RgltryRptg` |

## MT202 vs pacs.009

| **MT202 Tag** | **Meaning** | **pacs.009 Core (ISO 20022 XML Element)** |
|---------------|-------------|--------------------------------------------|
| `:20:` | Transaction Reference Number | `<FIToFICstmrCdtTrf><GrpHdr><MsgId>` or `<CdtTrfTxInf><PmtId><InstrId>` |
| `:21:` | Related Reference | `<CdtTrfTxInf><PmtId><EndToEndId>` or `<TxId>` *(usage depends on context)* |
| `:32A:` | Value Date, Currency, Amount | `<CdtTrfTxInf><IntrBkSttlmDt>` + `<IntrBkSttlmAmt Ccy="...">` |
| `:52A/D:` | Ordering Institution (Debtor Agent) | `<CdtTrfTxInf><DbtrAgt><FinInstnId><BICFI>` |
| `:53A/D:` | Sender’s Correspondent (optional) | `<CdtTrfTxInf><IntrmyAgt1><FinInstnId>` |
| `:54A/D:` | Receiver’s Correspondent (optional) | `<CdtTrfTxInf><IntrmyAgt2><FinInstnId>` |
| `:56A/D:` | Intermediary Institution (optional) | `<CdtTrfTxInf><IntrmyAgt3><FinInstnId>` |
| `:57A/D:` | Account With Institution (Creditor Agent) | `<CdtTrfTxInf><CdtrAgt><FinInstnId><BICFI>` |
| `:58A/D:` | Beneficiary Institution | `


## MT210 vs camt.050
| **MT210 Tag** | **Meaning** | **camt.050 (ISO 20022 XML Element)** |
|---------------|-------------|---------------------------------------|
| `:20:` | Transaction Reference Number | `<GrpHdr><MsgId>` *(message identifier)* or `<Ntfctn><Id>` |
| `:25:` | Account Identification (account to be credited) | `<Ntfctn><Acct><Id><IBAN>` or `<Othr><Id>` |
| `:32A:` | Value Date, Currency, Amount | `<Ntfctn><Ntry><ValDt><Dt>` + `<Amt Ccy="...">` |
| `:52A:` | Ordering Institution (originating bank) | `<Ntfctn><Ntry><NtryDtls><TxDtls><RltdPties><DbtrAgt>` |
| `:58A:` | Beneficiary Institution (account with bank) | `<Ntfctn><Ntry><NtryDtls><TxDtls><RltdPties><CdtrAgt>` |
| — | Message creation date/time (not explicit in MT210) | `<GrpHdr><CreDtTm>` |
| — | Number of transactions (not explicit in MT210) | `<GrpHdr><NbOfNtfctns>` |
| — | Statement/notification ID | `<Ntfctn><Id>` |


## 📑 CAMT.054 Key Tags & Sample Values  

| Tag / Element        | Example Value             | Meaning                                |
|----------------------|---------------------------|----------------------------------------|
| `<MsgId>`            | `NOTIF20240928`           | Unique message identifier              |
| `<CreDtTm>`          | `2025-09-28T10:15:00`     | Creation timestamp                     |
| `<Acct>/<IBAN>`      | `DE89370400440532013000`  | Customer account IBAN                  |
| `<Ccy>`              | `EUR`                     | Currency of account                    |
| `<Amt Ccy="EUR">`    | `1500.00`                 | Amount booked                          |
| `<CdtDbtInd>`        | `CRDT`                    | Credit (`DBIT` for debit)              |
| `<Sts>`              | `BOOK`                    | Booking status                         |
| `<BookgDt>/<Dt>`     | `2025-09-28`              | Booking date                           |
| `<ValDt>/<Dt>`       | `2025-09-28`              | Value date                             |
| `<InstrId>`          | `INSTR123456`             | Instruction ID                         |
| `<EndToEndId>`       | `E2E987654321`            | End-to-End reference                   |
| `<TxId>`             | `TX20250928001`           | Transaction ID                         |
| `<Dbtr>/<Nm>`        | `John Doe`                | Debtor (payer)                         |
| `<Cdtr>/<Nm>`        | `Corporate Customer GmbH` | Creditor (payee)                       |
| `<RmtInf>/<Ustrd>`   | `Invoice 1234 Payment`    | Remittance info (unstructured text)    |




## 📑 CAMT.057 Key Tags & Sample Values  

| Tag / Element        | Example Value             | Meaning                                               |
|----------------------|---------------------------|-------------------------------------------------------|
| `<MsgId>`            | `CXLREQ20250928`          | Unique message identifier                             |
| `<CreDtTm>`          | `2025-09-28T11:20:00`     | Creation timestamp                                    |
| `<Assgnmt>`          |                           | Assignment info (who is requesting whom)              |
| `<Assgnr>/<Agt>`     | BIC `BANKDEFFXXX`         | Assignor (party requesting cancellation, usually bank)|
| `<Assgne>/<Agt>`     | BIC `BANKUS33XXX`         | Assignee (party receiving cancellation request)       |
| `<CxlReqDtls>`       |                           | Block with payment(s) to be cancelled                 |
| `<TxId>`             | `TX20250928001`           | Original transaction identifier                       |
| `<PmtInstrId>`       | `PMT-12345`               | Original payment instruction ID                       |
| `<EndToEndId>`       | `INV-98765`               | End-to-end reference of original payment              |
| `<UETR>`             | `550e8400-e29b-41d4-a716-446655440000` | Unique End-to-End Transaction Reference (UUID) |
| `<Case>`             | `CASE20250928`            | Optional case identifier (if linked to case mgmt)     |
| `<Rsn>/<Cd>`         | `DUPL`                    | Reason for cancellation (e.g., DUPL = duplicate)      |
| `<AddtlInf>`         | `Duplicate payment, please cancel` | Free-text additional info                      |


