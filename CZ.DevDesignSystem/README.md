# CZ.DevDesignSystem

_A minimal Avalonia design system for modern .NET 9 applications._

CZ.DevDesignSystem provides a small but extendable foundation for Avalonia apps using the Fluent Design language.  
It includes theme-aware colors (light / dark), base styles for windows and buttons, and a soft, accessible color palette that feels more balanced than the default white/black contrast.

---

## ✨ Features

- 🌓 **Light / Dark mode** — automatic or programmatic theme switching with optimized Fluent color palettes
- 🎨 **App background brushes** — softer tones for better contrast perception
- 🔘 **Buttons** in three sizes (`small`, `regular`, `large`)
- ✍️ **Typography system** — Inter font with 8 predefined styles (h1-h6, p, small) using 1.125 scaling factor
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

---

## 🎨 Customization

### Typography

The design system uses the **Inter** font family with a modular type scale based on a 1.125 ratio (14px base):

| Style | Class | Font Size | Font Weight |
|-------|-------|-----------|-------------|
| Heading 1 | `.h1` | 28.38px | Bold |
| Heading 2 | `.h2` | 25.23px | Bold |
| Heading 3 | `.h3` | 22.43px | Bold |
| Heading 4 | `.h4` | 19.93px | SemiBold |
| Heading 5 | `.h5` | 17.72px | SemiBold |
| Heading 6 | `.h6` | 15.75px | SemiBold |
| Paragraph | `.p` | 14px | Normal |
| Small | `.small` | 12.44px | Normal |

Usage example:
```xml
<TextBlock Text="Main Title" Classes="h1" />
<TextBlock Text="Body text" Classes="p" />
<TextBlock Text="Fine print" Classes="small" />
```

### Button Sizes

Three button sizes are available via CSS classes:

```xml
<Button Content="Small" Classes="small" />
<Button Content="Regular" /> <!-- default -->
<Button Content="Large" Classes="large" />
```
