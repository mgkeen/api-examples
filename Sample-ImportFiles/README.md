# Rapptr File Formats

## Portfolio File

When uploading company structures and portfolios to Rapptr, we recommend that this is done at once using our CSV portfolio file template. You can find a [sample file here](https://github.com/fundapps/api-examples/blob/master/Sample-ImportFiles/Portfolios.csv) and a sample file with multiple aggregation structures [here](https://github.com/fundapps/api-examples/blob/master/Sample-ImportFiles/PortfoliosMultipleAggregationStructures.csv). For more guidance on how to structure your portfolio file, please refer to this [Help Centre article](https://fundapps.zendesk.com/hc/en-us/articles/210134023-Portfolio-File).

Please see [here](http://docs.fundapps.co/disclosureProperties.html#InstrumentProperties) for the portfolio file specs 

*PortfolioId* needs to be unique. In the scenario where a PortfolioId is uploaded which already exists in Rapptr, the previous portfolio details associated with that PortfolioId will be overridden, so if any columns are blank (e.g. disclosure form properties, then existing values will be overridden)

## Transaction Data

We accept transaction data in CSV format. You can find a [sample file here](Transactions.csv).

### File Column Detail

Column Name     | Data type          | Required | Length | Notes
----------------|--------------------|-------------------|--------|----------------------------
PortfolioId     | [String](https://github.com/fundapps/api-examples#data-types)             | X        | 255    |
AssetId         | [String](https://github.com/fundapps/api-examples#data-types)             | X        | 255    |
TransactionId   | [String](https://github.com/fundapps/api-examples#data-types)             | X        | 200    |
ExecutionDate   | [Date](https://github.com/fundapps/api-examples#data-types)  | X        |  -     | 
TransactionType | [String](https://github.com/fundapps/api-examples#data-types)             | X        |  -     | See below for valid options       
Price           | [Decimal](https://github.com/fundapps/api-examples#data-types)           | X        |  -     | Precision: 28; Scale: 8
Quantity        | [Decimal](https://github.com/fundapps/api-examples#data-types)            | X        |  -     | Precision: 28; Scale: 8
BrokerName      | [String](https://github.com/fundapps/api-examples#data-types)             |          |  255   | 

### Recognised Transaction Types

Type            | Description                                                                                 |
----------------|---------------------------------------------------------------------------------------------|
Buy             | A standard purchase / buy transaction                                                       |
Sell            | A standard sale /sell transaction                                                           |
CorporateAction | The issue of bonus shares, stock splits - everything related to actions taken by the issuer |
Expiry          | The expiry of a derivative contract                                                         |
Exercise        | The exercise of an option, future etc.                                                      |
Adjustment      | Internal transfer of Assets                                                                 |
Maturity        | The maturity of a convertible bond, for example                                             |
TakeOn          | Asset resulting from a new account being opened                                             |
Withdrawal      | Asset withdrawn due to an account being closed                                              |

### Data Requirements

- *TransactionId* needs to be unique. In the scenario where a TransactionId is uploaded which already exists in Rapptr, this will result in a validation error.
- *AssetId* and *PortfolioId* values need to match the fields with the same name in Position data; this is key in order to be able to query the correct transactions for disclosure forms.


## Issuer Register Data

We accept issuer register data in CSV format. You can find a [sample file here](https://github.com/fundapps/api-examples/blob/master/Sample-ImportFiles/Issuer%20Register.csv).

### File Column Detail

Column Name                       | Description |Data type | Required | Length  
----------------------------------|-------------|-------------------|-------------------|--------
Id                                | The IssuerId that is currently used in your position file | [String](https://github.com/fundapps/api-examples#data-types)             | X          | 255    
Name                              | The legal name of the issuer. This field could refer to the IssuerName that is currently used in your position file | [String](https://github.com/fundapps/api-examples#data-types)             | X          | 255    
Address                           | The issuer's address | [String](https://github.com/fundapps/api-examples#data-types)             | X          | 255    
City                              | The city the issuer is located | [String](https://github.com/fundapps/api-examples#data-types)             | X          | 255    
Province                          | The province of the issuer (if any) | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255    
PostCode                          | The post code of the issuer (if any) | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255    
Country                           | The country the issuer is located | [String](https://github.com/fundapps/api-examples#data-types)             | X          | 255  
ContactPerson                     | The primary issuer contact | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255   
ContactPersonPosition             | The primary issuer contact's position | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
EmailAddress                      | The primary issuer contact's email address | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
TelephoneNumber                   | The primary issuer contact's telephone number | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255      
AustralianCompanyNumber           | The Australian Company Number (ACN) is a unique, nine-digit number. Under the Corporations Act 2001, every company in Australia has been issued an ACN to ensure adequate identification of companies when transacting business | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
AustralianRegisteredSchemeNumber  | The Australian Registered Scheme Number (ARSN) is a nine digit number issued to Australian managed investment schemes by Australian Securities and Investments Commission. | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
SouthAfricanRegistrationNumber    | The South African company registration number | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
IssuersRegisterCourt              | German company registration court. For more information consult or more information consult     [Germany's Company Register](https://www.unternehmensregister.de/ureg/search1.2.html;jsessionid=0198670396BF01C2137968DEEC63C8CE.web01-1?submitaction=language&language=en) | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
RegisterType                      | German company registeration type. Possible values could include: Cooperative Register, Commercial Register Excerpt, Commercial Register, Partnership Register. For more information consult [Germany's Company Register](https://www.unternehmensregister.de/ureg/search1.2.html;jsessionid=0198670396BF01C2137968DEEC63C8CE.web01-1?submitaction=language&language=en) | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
RegisterNumber                    | The German company registeration number | [String](https://github.com/fundapps/api-examples#data-types)             |           | 255     
PhilippineSecId             | The identification number issued by the Securities and Exchange Commission in the Philippines | [String](https://github.com/fundapps/api-examples#data-types) | | 255 
PhilippineBirTaxId          | The company tax identification number issued by the Bureau of Internal Revenue (BIR) | [String](https://github.com/fundapps/api-examples#data-types) | | 255 

### Data Requirements

- *Id* (or IssuerId) needs to be unique. In the scenario where an IssuerId is uploaded which already exists as part of the Issuer Register, this will result in a validation error.
- the *Id* value needs to match the IssuerId field the Position file; this is key in order to be able to query the correct issuer information for disclosure forms.

## Imported Disclosures
We accept information about imported disclosures in CSV format. You can find a [sample file here](https://github.com/fundapps/api-examples/blob/master/Sample-ImportFiles/Imported%20Disclosures.csv). Unlike the the other import files, these should be sent to support@fundapps.co as we upload directly into the databases.  

### File Column Detail

Column Name                       | Data type | Required | Length  | Notes
----------------------------------|--------------------|-------------------|---------|--------
RapptrRuleID                      | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | ID of the rule for which this disclosure was made
AggregationStructure              | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | The aggregation structure where the rule triggered on
PortfolioOrEntityID               | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | ID of portfolio/entity where the rule triggered
ISIN                              | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | ISIN of the instrument which triggered the rule
IssuerID                          | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | ID of the issuer
IssuerName                        | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | Name of the issuer 
OwnershipPercentageAtFiling       | [String](https://github.com/fundapps/api-examples#data-types)             | X        | -       | Inputting 6.2 here is equivalent to 6.2%
DisclosureDate                    | [Date](https://github.com/fundapps/api-examples#data-types)  | X        |  -      | Date of disclosure filing


### Data Requirements

- IssuerId needs to be needs to be consistent throughout time so that the system can link the imported disclosure to another disclosurein the future.
