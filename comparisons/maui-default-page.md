# A default new .NET MAUI page

This is what a default new page for .NET MAUI looks like in XAML:

```xaml
<?xml version="1.0" encoding="utf-8" ?>
<ContentPage xmlns="http://schemas.microsoft.com/dotnet/2021/maui"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="MauiApp1.MainPage">

    <ScrollView>
        <VerticalStackLayout
            Padding="30,0"
            Spacing="25">
            <Image
                Source="dotnet_bot.png"
                HeightRequest="185"
                Aspect="AspectFit"
                SemanticProperties.Description="dot net bot in a hovercraft number nine" />

            <Label
                Text="Hello, World!"
                Style="{StaticResource Headline}"
                SemanticProperties.HeadingLevel="Level1" />

            <Label
                Text="Welcome to &#10;.NET Multi-platform App UI"
                Style="{StaticResource SubHeadline}"
                SemanticProperties.HeadingLevel="Level2"
                SemanticProperties.Description="Welcome to dot net Multi platform App U I" />

            <Button
                x:Name="CounterBtn"
                Text="Click me" 
                SemanticProperties.Hint="Counts the number of times you click"
                Clicked="OnCounterClicked"
                HorizontalOptions="Fill" />
        </VerticalStackLayout>
    </ScrollView>

</ContentPage>
```

This is the exact same thing in equivalent ENAMEL:

```ascii
ContentPage 
    ScrollView
        VerticalStackLayout
            Padding=30,0
            Spacing=25

            Image dotnet_bot.png
                HeightRequest=185
                Aspect=AspectFit
                SemanticProperties.Description="dot net bot in a hovercraft number nine"

            Label "Hello, World!"
                Style={Headline}
                SemanticProperties.HeadingLevel=Level1

            Label "Welcome to &#10;.NET Multi-platform App UI"
                Style={SubHeadline}
                SemanticProperties.HeadingLevel=Level2
                SemanticProperties.Description="Welcome to dot net Multi platform App U I"

            Button "Click me" 
                x:Name=CounterBtn
                SemanticProperties.Hint="Counts the number of times you click"
                Clicked=OnCounterClicked
                HorizontalOptions=Fill
```

The XAML was 1316 characters over 36 lines.  
The ENAMEL is 887 characters over 25 lines.

---

A better version of the ENAMEL (as could easily be created by a developer with XAML experience) could look like this.

```ascii
VerticallyScrollingPage

    Image dotnet_bot.png
        HeightRequest=185
        SemanticProperties.Description="dot net bot in a hovercraft number nine"

    Headline "Hello, World!"

    SubHeadline "Welcome to &#10;.NET Multi-platform App UI"
        SemanticProperties.Description="Welcome to dot net Multi platform App U I"

    Button "Click me"
        SemanticProperties.Hint="Counts the number of times you click"
        Clicked=OnCounterClicked
```

This still produces the exact same output (while relying on simple styles and classes specified elsewhere) but is only 458 characters over 14 lines.  
This is less than 40% the size of the original XAML but is more readable and easier to understand.
