# A new .NET MAUI page with sample content

This is what a new page containing the SyncFusion sample content for .NET MAUI looks like in XAML:

```xaml
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:pageModels="clr-namespace:MauiApp1.PageModels"             
             xmlns:models="clr-namespace:MauiApp1.Models"
             xmlns:controls="clr-namespace:MauiApp1.Pages.Controls"
             xmlns:pullToRefresh="clr-namespace:Syncfusion.Maui.Toolkit.PullToRefresh;assembly=Syncfusion.Maui.Toolkit"
             xmlns:toolkit="http://schemas.microsoft.com/dotnet/2022/maui/toolkit"
             x:Class="MauiApp1.Pages.MainPage"
             x:DataType="pageModels:MainPageModel"
             Title="{Binding Today}">

    <ContentPage.Behaviors>
        <toolkit:EventToCommandBehavior
                EventName="NavigatedTo"
                Command="{Binding NavigatedToCommand}" />
        <toolkit:EventToCommandBehavior
                EventName="NavigatedFrom"
                Command="{Binding NavigatedFromCommand}" />
        <toolkit:EventToCommandBehavior
                EventName="Appearing"                
                Command="{Binding AppearingCommand}" />
    </ContentPage.Behaviors>

    <ContentPage.Resources>
        <ResourceDictionary>
            <toolkit:InvertedBoolConverter x:Key="InvertedBoolConverter" />
        </ResourceDictionary>
    </ContentPage.Resources>

    <Grid>
        <pullToRefresh:SfPullToRefresh
            IsRefreshing="{Binding IsRefreshing}"
            RefreshCommand="{Binding RefreshCommand}">
            <pullToRefresh:SfPullToRefresh.PullableContent>
                <ScrollView>
                    <VerticalStackLayout Spacing="{StaticResource LayoutSpacing}" Padding="{StaticResource LayoutPadding}">
                        <controls:CategoryChart />
                        <Label Text="Projects" Style="{StaticResource Title2}"/>
                        <ScrollView Orientation="Horizontal" Margin="-30,0">
                            <HorizontalStackLayout 
                                Spacing="15" Padding="30,0"
                                BindableLayout.ItemsSource="{Binding Projects}">
                                <BindableLayout.ItemTemplate>
                                    <DataTemplate x:DataType="models:Project">
                                        <controls:ProjectCardView WidthRequest="200">
                                            <controls:ProjectCardView.GestureRecognizers>
                                                <TapGestureRecognizer Command="{Binding NavigateToProjectCommand, Source={RelativeSource AncestorType={x:Type pageModels:MainPageModel}}, x:DataType=pageModels:MainPageModel}" CommandParameter="{Binding .}"/>
                                            </controls:ProjectCardView.GestureRecognizers>
                                        </controls:ProjectCardView>
                                    </DataTemplate>
                                </BindableLayout.ItemTemplate>
                            </HorizontalStackLayout>
                        </ScrollView>
                        <Grid HeightRequest="44">
                            <Label Text="Tasks" Style="{StaticResource Title2}" VerticalOptions="Center"/>
                            <ImageButton 
                                Source="{StaticResource IconClean}"
                                HorizontalOptions="End"
                                VerticalOptions="Center"
                                Aspect="Center"
                                HeightRequest="44"
                                WidthRequest="44"
                                IsVisible="{Binding HasCompletedTasks}"
                                Command="{Binding CleanTasksCommand}"
                                />
                        </Grid>
                        <VerticalStackLayout Spacing="15"
                            BindableLayout.ItemsSource="{Binding Tasks}">
                            <BindableLayout.ItemTemplate>
                                <DataTemplate>
                                    <controls:TaskView TaskCompletedCommand="{Binding TaskCompletedCommand, Source={RelativeSource AncestorType={x:Type pageModels:MainPageModel}}, x:DataType=pageModels:MainPageModel}" />
                                </DataTemplate>
                            </BindableLayout.ItemTemplate>
                        </VerticalStackLayout>
                    </VerticalStackLayout>
                </ScrollView>
            </pullToRefresh:SfPullToRefresh.PullableContent>
        </pullToRefresh:SfPullToRefresh>

        <controls:AddButton 
            IsEnabled="{Binding IsBusy, Converter={StaticResource InvertedBoolConverter}}"
            Command="{Binding AddTaskCommand}" />
    </Grid>
</ContentPage>
```

And here's the direct equivalent in ENAMEL:

```xaml
ContentPage x:DataType="pageModels:MainPageModel"
            Title="{Binding Today}"
            NavigatedTo="@ NavigatedToCommand.Invoke(); @"
            NavigatedFrom="@ NavigatedFromCommand.Invoke(); @"
            Appearing="@ AppearingCommand.Invoke(); @"

    .Resources
        toolkit:InvertedBoolConverter x:Key="InvertedBoolConverter"

    Grid
        pullToRefresh:SfPullToRefresh
            IsRefreshing={IsRefreshing}
            RefreshCommand={RefreshCommand}
            .PullableContent
                ScrollView
                    VerticalStackLayout Spacing="{StaticResource LayoutSpacing}" Padding="{StaticResource LayoutPadding}"
                        controls:CategoryChart 

                        Label Text="Projects" Style="{StaticResource Title2}"

                        ScrollView Orientation=Horizontal Margin="-30,0"
                            HorizontalStackLayout 
                                Spacing=15 Padding="30,0"
                                BindableLayout.ItemsSource={Projects}
                                    .ItemTemplate
                                        DataTemplate x:DataType="models:Project"
                                            controls:ProjectCardView WidthRequest="200"
                                                .GestureRecognizers
                                                    TapGestureRecognizer Command="{NavigateToProjectCommand, Source={RelativeSource AncestorType={x:Type pageModels:MainPageModel}}, x:DataType=pageModels:MainPageModel}" CommandParameter={.} 

                        Grid HeightRequest="44"
                            Label "Tasks" Style="{StaticResource Title2}" VerticalOptions=Center

                            ImageButton 
                                Source="{StaticResource IconClean}"
                                HorizontalOptions=End
                                VerticalOptions&Aspect=Center
                                HeightRequest&WidthRequest=44
                                IsVisible={HasCompletedTasks}
                                Command={CleanTasksCommand}

                        VerticalStackLayout Spacing="15" BindableLayout.ItemsSource="{Tasks}"
                            BindableLayout.ItemTemplate
                                controls:TaskView
                                    TaskCompletedCommand="{TaskCompletedCommand, Source={RelativeSource AncestorType={x:Type pageModels:MainPageModel}}, x:DataType=pageModels:MainPageModel}"

        controls:AddButton {AddTaskCommand} 
            IsEnabled="{IsBusy, Converter={StaticResource InvertedBoolConverter}}"
```

The 85 lines of XAML can be represented in just 49 lines of ENAMEL.

This is a direct comparison with what is in the default templates.  
However, both could be made significantly simpler and more maintainable by applying good coding practices, but this is beyond the scope of this document.
