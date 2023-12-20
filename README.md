You can customize the .NET MAUI SfExpander header icon in the SfExpander.Header elements using the converter.

**XAML**

Binding the [IsExpanded](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.Expander.SfExpander.html#Syncfusion_Maui_Expander_SfExpander_IsExpanded) property to show different icons to expand and collapse. Set [HeaderIconPosition](https://help.syncfusion.com/cr/maui/Syncfusion.Maui.Expander.SfExpander.html#Syncfusion_Maui_Expander_SfExpander_HeaderIconPosition) to None to hide the default header icon.

```
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:syncfusion="clr-namespace:Syncfusion.Maui.Expander;assembly=Syncfusion.Maui.Expander"   
             xmlns:local="clr-namespace:ExpanderMAUI"
             x:Class="ExpanderMAUI.MainPage">
    
    <ContentPage.Resources>
        <ResourceDictionary>
            <local:ExpanderIconConverter x:Key="ExpanderIconConverter"/>
        </ResourceDictionary>
    </ContentPage.Resources>
    
    <ScrollView BackgroundColor="#EDF2F5" Padding="0,30,0,0">
        <StackLayout>
            <syncfusion:SfExpander x:Name="expander1" HeaderIconPosition="None">
                <syncfusion:SfExpander.Header>
                    <Grid HeightRequest="50">
                        <Label TextColor="#495F6E" Text="Veg Pizza" Padding="5,0,0,0" />
                        <Image Margin="10" HorizontalOptions="End" Source="{Binding IsExpanded,Source={x:Reference expander1},Converter={StaticResource ExpanderIconConverter}}" HeightRequest="20" WidthRequest="20"/>
                    </Grid>
                </syncfusion:SfExpander.Header>
                <syncfusion:SfExpander.Content>
                    <Grid Padding="10,10,10,10">
                        <Label TextColor="#303030" Text="Veg pizza is prepared with the items that meet vegetarian standards by not including any meat or animal tissue products." HeightRequest="50" VerticalTextAlignment="Center" />
                    </Grid>
                </syncfusion:SfExpander.Content>
            </syncfusion:SfExpander>


            <syncfusion:SfExpander x:Name="expander2" HeaderIconPosition="None">
                <syncfusion:SfExpander.Header>
                    <Grid HeightRequest="50">
                        <Label TextColor="#495F6E" Text="Non-veg Pizza" Padding="5,0,0,0" />
                        <Image Margin="10" HorizontalOptions="End" Source="{Binding IsExpanded,Source={x:Reference expander2},Converter={StaticResource ExpanderIconConverter}}" HeightRequest="20" WidthRequest="20"/>
                    </Grid>
                </syncfusion:SfExpander.Header>
                <syncfusion:SfExpander.Content>
                    <Grid Padding="10,10,10,10">
                        <Label TextColor="#303030" Text="Non-veg pizza is prepared by including the meat and animal tissue products." HeightRequest="50" VerticalTextAlignment="Center" />
                    </Grid>
                </syncfusion:SfExpander.Content>
            </syncfusion:SfExpander>
        </StackLayout>
    </ScrollView>
</ContentPage>
```

**C#**

Return image based on the **IsExpanded** property value.

```
public class ExpanderIconConverter : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        if ((bool)value)
            return "arrowdown.png";
        else
            return "arrowup.png";
    }

    public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
    {
        throw new NotImplementedException();
    }
}
```
