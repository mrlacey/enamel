# A default new WinUI Window

This is what the MainWindow of a new WinUI app looks like in XAML:

_Note. The latest templates do not include the StackPanel and button, but they are included here to show a variation from the WPF comparison example._

```xaml
<?xml version="1.0" encoding="utf-8"?>
<Window
    x:Class="App1.MainWindow"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:App1"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d"
    Title="App1">

    <StackPanel Orientation="Horizontal" HorizontalAlignment="Center" VerticalAlignment="Center">
        <Button x:Name="myButton" Click="myButton_Click">Click Me</Button>
    </StackPanel>
</Window>
```

And the equivalent ENAMEL:

```ascii
Window Title=App1

    StackPanel Orientation=Horizontal HorizontalAlignment&VerticalAlignment=Center

        Button x:Name="myButton" Click="@ myButton.Content = "Clicked"; @"
            .Content
                Click Me
```

Note also that the ENAMEL version also removes the need for the EventHandler in the XAML code-behind files.
