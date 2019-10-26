# Create MF Portfolio.JSON File
## Summary
The `MF Portfolio.JSON` file contains details of the funds you have invested in along with all the transactions you've made in every fund. The file also contains API keys needed to run the notebook. You need to create and save with JSON before running the notebook.

## Steps to create the file

### Create Quandl account.
Quandl API lets you download financial information of various funds. The script depends heavily on this API in order to get the information.
1. Visit https://www.quandl.com and Sign Up for an account
2. Go To Account Settings, you can view your API key. Make note of it as it is required to be a part of JSON file.

### Get Consolidated Account Statement
Get your current portfolio summary pdf from Karvy. Karvy MF services provides consolidated account statement from most major MF providers.
  1. Visit `https://karvymfs.com/investor/General/ConsolidatedAccountStatement`
  2. Select Detailed in Statement Type
  3. Select from date as date of your first investment ever in MF and End Date as today's date
  4. Enter PAN number, email id and create a password. Note: This password will be required everytime you want to open your PDF.
  5. Click Submit button. You'll receive your statement in the mail provided soon.
  6. Download and Open PDF with password provided by you.

### Create JSON
1. Duplicate `MF Portfolio - Template.json` as `MF Portfolio.JSON`
2. Open `MF Portfolio.JSON` and start editing the file.
3. Following block contains meaning of each field along with accepted value

```
  Account Holder Name - Portfolio Holder Name as a string. Example value: "John Doe"
  PAN - PAN card number. Not  required in code. It is added for traceability of investor. Example value "DLOPK9114A"
  Last Updated - Date on which this file was last edited. To keep track and not open previous version of this file. Date is stored as string in "YYYY-MM-DD" format. Example Value: "2019-10-26",
  Quandl API Key - Quandl API key copied in step above as a string. Example value: "ooyxAKfCTmnE7JgBAqw2"
  Funds - Array of JSONs
  [
    {
      Fund Name - Fund name as String. Example value: "SBI Banking and Financial Services Fund - Direct Plan - Growth",
      ID - Search the fund name keywords on Quandl and copy the ID as string here. Example value: "AMFI/133859",
      Tags - Array of string. Example value: ["Equity", "Sectoral-Banking"],
      Lock In": JSON containing lock in period Example value:
      {
        Period - Int about Lock in period in months. Example value: 0
      }
      Exit Load - JSON containing lock in period Example value:  
      {
        Period - Int about Lock in period in months before which Load percentage is deducted. Example value: 12,
        Load - Int containing percentage of amount that'll be deducted on checkout. Example value: 1
      },
      Tax Implication - JSON containing long term and short term tax implications in percentage. Example value:
      {
        Long Term - Int value of long term tax implications. Example value: 10,
        Short Term - Int value of short term tax implications. Example value: 15
      },
      Transactions - Array of transaction json.
      [
        {
          Date - Transaction date as string in "YYYY-MM-DD" format. Example value: "2019-10-03"
          Type -  Type of transaction as string. Value "Purchase" or "Sell"
          Amount -  Amount invested or disinvested in Rs. Example value: 5000,
          Units -  Units purchased or sold. Example value: 234,
          NAV -  NAV at time or transaction. Example value: 21.367
        }
      ]
    }
  ]
}

```
