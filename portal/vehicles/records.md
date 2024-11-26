# Vehicle Records
Records allow you to track various actions taken on a particular vehicle. The data stored in records is used by the Portal to create statics such as average fuel economy, estimated oil change date, etc.

[toc]

## Odometer Records
Odometer records help provide the Portal with information where there would usually be none, and allows for more accurate predictions to be made. For example, if you have a short commute to work, but take long trips often and only create fuel records, your average daily mileage will be skewed because the Portal has fewer date intervals to calculate miles driven. If you add daily or weekly odometer readings, the Portal will have more date intervals to use when calculating average daily mileage.

## Fuel Records
Fuel records contain the following information:
- Odometer (required)
- Fuel amount in gallons (required)
- Fuel cost (required)
- Fuel octane
- Fuel ethanol content, represented as a percentage of the total fuel content
- Location
- Date (YYYY-mm-dd format)
- Attachments (images, receipts, etc)

This information is used together to calculate average fuel economy (in mpg and miles per tank.)

With many fuel records, you will be able to see the lifetime fuel amount and cost for the vehicle, and average price per gallon. You will also be able to see how many times you've refuelled at a particular station, and what the lowest, highest, and average price is for that station.

### How does the Portal calculate fuel economy?
The following formula is used to calculate fuel economy:  
`Miles Driven = Last Fill Odometer - Current Odometer`  
`Fuel Economy = Miles Driver / Last Fill Amount`  
The resulting fuel economy is rounded to the nearest decimal place.

Because it is not possible for the Portal to know how much fuel has been consumed between two particular records, nor how much fuel remains in the tank after a particular record, you will get the most accurate results if each fuel refill fills the tank. It doesn't matter what the level in the tank was before the refill, as long as it makes it to full. If you only partially fill the tank, the fuel economy prediction will not be accurate.

## Oil Change Records
Oil change records contain the following information:
- Odometer (required)
- Oil weight
- Oil amount
- Oil filter part number
- Desired miles until next oil change
- Date (formatted YYYY-mm-dd)
- Attachments (images, receipts, etc)

Oil change record data is used to help you plan when your next oil change needs to be done. The vehicle overview page will use your daily average mileage to determine how soon an oil change should occur, based on your desired miles to next oil change. By default, the oil change interval is 7,500 miles.

## Generic
Generic records containt the following information:
- Odometer (required)
- Date (formatted YYYY-mm-dd)
- Type (required)
  - Note
  - Service
  - Repair
  - Issue
  - Modification
  - Upgrade
- Title (required)
- Notes
- Attachments (images, receipts, etc)

Aside from odometer, the information in this type of record is not used by the Portal for any calculations.
