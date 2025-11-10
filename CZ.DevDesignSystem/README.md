# CZ.DevDesignSystem

_A minimal Avalonia design system for modern .NET 9 applications._

CZ.DevDesignSystem provides a small but extendable foundation for Avalonia apps using the Fluent Design language.  
It includes theme-aware colors (light / dark), base styles for windows and buttons, and a soft, accessible color palette that feels more balanced than the default white/black contrast.

---

## ✨ Features

- 🌓 **Light / Dark mode** — automatic or programmatic theme switching
- 🎨 **App background brushes** — softer tones for better contrast perception
- 🔘 **Buttons** in two sizes (`regular`, `small`)
- 🧱 **Fluent-based foundation** — keeps native Avalonia Fluent controls compatible
- 📦 **NuGet package ready** — easy to integrate into other projects

---

## 🚀 Getting Started

### 1. Install via NuGet

Add the package reference to your Avalonia App project:

```bash
dotnet add package CZ.DevDesignSystem --version 0.1.0
```

### 2. Example Integration into an Avalonia MVVM App

#### App.axaml
```xml
<Application xmlns="https://github.com/avaloniaui"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             x:Class="YourApp.App">
    <Application.Styles>
        <StyleInclude Source="avare://AvaloniaUI.Themes.Fluent/FluentTheme.xaml" />
        <StyleInclude Source="avare://CZ.DevDesignSystem/Themes/Styles.axaml" />
    </Application.Styles>
</Application>
```

#### MainWindow.axaml
```xml
<Window xmlns="https://github.com/avaloniaui"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:vm="using:YourApp.ViewModels"
        x:Class="YourApp.Views.MainWindow"
        x:DataType="vm:MainWindowViewModel"
        Title="My MVVM App"
        Width="800"
        Height="600">

    <StackPanel Margin="20" Spacing="10">
        <TextBlock Text="{Binding Title}"
                   FontSize="24"
                   FontWeight="Bold" />

        <TextBlock Text="{Binding Description}"
                   TextWrapping="Wrap" />

        <Button Content="Click Me"
                Command="{Binding OnClickCommand}"
                Classes="regular" />

        <Button Content="Small Button"
                Command="{Binding OnSmallClickCommand}"
                Classes="small" />
    </StackPanel>
</Window>
```

#### MainWindowViewModel.cs
```csharp
using System.Windows.Input;
using ReactiveUI;

namespace YourApp.ViewModels;

public class MainWindowViewModel : ViewModelBase
{
    public string Title => "Welcome to CZ.DevDesignSystem";
    public string Description => "This app uses the design system with automatic theme switching.";

    public ICommand OnClickCommand { get; }
    public ICommand OnSmallClickCommand { get; }

    public MainWindowViewModel()
    {
        OnClickCommand = ReactiveCommand.Create(() =>
        {
            // Handle click
        });

        OnSmallClickCommand = ReactiveCommand.Create(() =>
        {
            // Handle small button click
        });
    }
}
```
