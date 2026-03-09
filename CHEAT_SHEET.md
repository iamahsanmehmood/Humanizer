# Humanizer Quick Reference — C# Cheat Sheet 🧩

> A practical quick-reference for the most common Humanizer operations in C#/.NET projects.

## 📦 Installation

```bash
dotnet add package Humanizer
```

## 🔤 String Humanization

```csharp
// PascalCase / camelCase → Sentence
"PascalCaseString".Humanize();          // → "Pascal case string"
"camelCaseString".Humanize();           // → "Camel case string"
"ALLCAPS".Humanize();                   // → "ALLCAPS"

// Underscored → Sentence  
"some_title".Humanize();                // → "Some title"
"some_title".Humanize(LetterCasing.Title); // → "Some Title"
```

## 📅 DateTime Humanization

```csharp
DateTime.UtcNow.AddHours(-2).Humanize();   // → "2 hours ago"
DateTime.UtcNow.AddDays(1).Humanize();     // → "tomorrow"
DateTime.UtcNow.AddDays(-1).Humanize();    // → "yesterday"
DateTime.UtcNow.AddMonths(-3).Humanize();  // → "3 months ago"
```

## ⏱️ TimeSpan Humanization

```csharp
TimeSpan.FromMinutes(90).Humanize();       // → "1 hour, 30 minutes"
TimeSpan.FromDays(14).Humanize();          // → "2 weeks"
TimeSpan.FromMilliseconds(1234).Humanize();// → "1 second"

// Precision control
TimeSpan.FromDays(16).Humanize(2);         // → "2 weeks, 2 days"
```

## 🔢 Number Humanization

```csharp
// Number to words
1.ToWords();        // → "one"
42.ToWords();       // → "forty-two"
1234.ToWords();     // → "one thousand two hundred and thirty-four"

// Ordinals
1.Ordinalize();     // → "1st"
2.Ordinalize();     // → "2nd"
23.Ordinalize();    // → "23rd"

// Number to ordinal words
1.ToOrdinalWords(); // → "first"
5.ToOrdinalWords(); // → "fifth"
```

## 📊 Quantity Humanization

```csharp
"file".ToQuantity(1);   // → "1 file"
"file".ToQuantity(5);   // → "5 files"
"person".ToQuantity(0); // → "0 people"
```

## 📐 Byte Size

```csharp
(1024).Bytes().ToString();           // → "1 KB"
(1048576).Bytes().ToString();        // → "1 MB"
(1073741824).Bytes().Humanize();     // → "1 GB"

// From specific units
(10).Megabytes().ToString();         // → "10 MB"
(10).Megabytes().Humanize("GB");     // → "0.01 GB"
```

## 🎯 Truncation

```csharp
"Long string with many characters".Truncate(10);           // → "Long str…"
"Long string".Truncate(10, Truncator.FixedNumberOfWords);  // → "Long…"
```

## 🌍 Localization

Humanizer supports 40+ languages:

```csharp
// Configure for Urdu
using Humanizer.Configuration;
Configurator.DateTimeHumanizeStrategy = new DefaultDateTimeHumanizeStrategy();
```

---

*Contributed by [Ahsan Mehmood](https://github.com/iamahsanmehmood) — [XechTech](https://xechtech.com)*
