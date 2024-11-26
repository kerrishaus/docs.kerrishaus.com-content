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

With many fuel records, you will be able to see the lifetime fuel amount and cost for the vehicle, and average price per gallon. You will also be able to see how many times you've refuelled at a particular station, and what the lowest, highest, and average price is for that station.

### How does the Portal calculate fuel economy?
The following formula is used to calculate fuel economy:  
`Miles Driven = Last Fill Odometer - Current Odometer`  
`Fuel Economy = Miles Driver / Last Fill Amount`  
The resulting fuel economy is rounded to the nearest decimal place.

Because it is not possible for the Portal to know how much fuel has been consumed between two particular records, nor how much fuel remains in the tank after a particular record, you will get the most accurate results if each fuel refill fills the tank. It doesn't matter what the level in the tank was before the refill, as long as it makes it to full. If you only partially fill the tank, the fuel economy prediction will not be accurate.
