<!-- default file list -->
*Files to look at*:

* [MainPage.xaml](./CS/ManualDataUpdates/MainPage.xaml) (VB: [MainPage.xaml](./VB/ManualDataUpdates/MainPage.xaml))
* [MainPage.xaml.cs](./CS/ManualDataUpdates/MainPage.xaml.cs) (VB: [MainPage.xaml](./VB/ManualDataUpdates/MainPage.xaml))
<!-- default file list end -->
# How to make many updates per second


<p>If the grid's DataSource is updated quite often (for instance, 100 times per second), the grid itself does not have time to finish its updates. To prevent an unresponsive state, or any artifacts, we suggest the following technique to receive many updates.</p><p>Assign the IList DataSource to the GridControl.DataSource. By default, the IList collection does not send any notification about changes, to the GridControl (objects in the collection should not implement the INotifyPropertyChanged interface either). As a result, the GridControl will not perform any updates until you call the RefreshData method.</p><p>Another approach is to create two collections. The first one should be assigned to the GridControl.DataSource, and the second one should be updated when necessary. Then when the application is in the idle state, synchronize the GridControl.DataSource collection with the second collection (use the BeginDataUpdate/EndDataUpdate methods to improve the grid's performance).</p>

<br/>


