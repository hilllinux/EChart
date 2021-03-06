#EChart
A highly **extendable**, easy to use chart with **event handling**, **animation** supported. 


[![](https://dl.dropboxusercontent.com/s/px1zz1ofxbzrpci/EChart.gif)](https://dl.dropboxusercontent.com/s/px1zz1ofxbzrpci/EChart.gif)

## How To Use
### Step 1
Download project [here](https://github.com/zhuhuihuihui/EChart)

And Drag `/EChart/` folder into your project

### Step 2
Import the head file:

	#import "EColumnChart.h"
	
Make your ViewController adopts the EColumnChart's protocal:

	@interface YourViewController : UIViewController <EColumnChartDelegate, EColumnChartDataSource>
	
Declare a EColumnChart instance:
	
	@property (strong, nonatomic) EColumnChart *eColumnChart;

### Step 3
Give your EColumnChart a nice frame:

	_eColumnChart = [[EColumnChart alloc] initWithFrame:CGRectMake(40, 100, 250, 200)];
	
Set EColumnChart's delegate and dataSource to your ViewController:

	[_eColumnChart setDelegate:self];
    [_eColumnChart setDataSource:self];
    
Add EColumnChart to wherever you want:

    [self.view addSubview:_eColumnChart];
    
## Provide data & Get events
After setting up your EColumnChart, you may need to provide the data for the EColumnChart and you will be able to get events from EColumnChart as well.

If you were a expert with `UITableView`, you will be quite familier with the way `EColumnChart` works. Because they work in a same way.

### DataSource  
You need to implement every method in the `EColumnChartDataSource`

	/** How many Columns are there in total.*/
	- (NSInteger) numberOfColumnsInEColumnChart:(EColumnChart *) eColumnChart;

	/** How many Columns should be presented on the screen each time*/
	- (NSInteger) numberOfColumnsPresentedEveryTime:(EColumnChart *) eColumnChart;

	/** The hightest vaule among the whole chart*/
	- (EColumnDataModel *)     highestValueEColumnChart:(EColumnChart *) eColumnChart;

	/** Value for each column*/
	- (EColumnDataModel *)     eColumnChart:(EColumnChart *) eColumnChart
                        valueForIndex:(NSInteger)index;
                        
### EColumnChartDelegate 
The implementation of the Delegate is according to your needs

	/** When finger single taped the column*/
	- (void)        eColumnChart:(EColumnChart *) eColumnChart
             didSelectColumn:(EColumn *) eColumn;

	/** When finger enter specific column, this is dif from tap*/
	- (void)        eColumnChart:(EColumnChart *) eColumnChart
        fingerDidEnterColumn:(EColumn *) eColumn;

	/** When finger leaves certain column, will tell you which column you are leaving*/
	- (void)        eColumnChart:(EColumnChart *) eColumnChart
        fingerDidLeaveColumn:(EColumn *) eColumn;

	/** When finger leaves wherever in the chart, will trigger both if finger is leaving from a column */
	- (void) fingerDidLeaveEColumnChart:(EColumnChart *)eColumnChart;
