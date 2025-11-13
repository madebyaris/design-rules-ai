# Apple HIG - Typography

## iOS/iPadOS Typography

### Font Family
- **SF Pro**: System font (iOS 9+)
- **SF Pro Rounded**: Rounded variant
- **SF Mono**: Monospaced font
- **New York**: Serif font (optional)

### Text Styles (Dynamic Type)

#### Large Titles
- **Large Title**: 34pt, weight: regular/bold

#### Titles
- **Title 1**: 28pt, weight: regular/bold
- **Title 2**: 22pt, weight: regular/bold
- **Title 3**: 20pt, weight: regular/semibold

#### Headlines
- **Headline**: 17pt, weight: semibold

#### Body
- **Body**: 17pt, weight: regular
- **Callout**: 16pt, weight: regular

#### Subheadlines
- **Subheadline**: 15pt, weight: regular
- **Footnote**: 13pt, weight: regular

#### Captions
- **Caption 1**: 12pt, weight: regular
- **Caption 2**: 11pt, weight: regular

### Font Weights
- **Ultralight**: 100
- **Thin**: 200
- **Light**: 300
- **Regular**: 400
- **Medium**: 500
- **Semibold**: 600
- **Bold**: 700
- **Heavy**: 800
- **Black**: 900

## macOS Typography

### Text Styles
- **Large Title**: 26pt
- **Title 1**: 22pt
- **Title 2**: 17pt
- **Title 3**: 15pt
- **Headline**: 13pt, weight: bold
- **Body**: 13pt
- **Callout**: 12pt
- **Subheadline**: 11pt
- **Footnote**: 10pt
- **Caption 1**: 10pt
- **Caption 2**: 10pt

## Dynamic Type
- Supports user's preferred text size
- 7 standard sizes + 5 accessibility sizes
- Always use text styles, not fixed sizes
- Test with largest accessibility sizes

## SF Pro Features

### Optical Sizes
- **Text**: < 20pt (optimized for small sizes)
- **Display**: ≥ 20pt (optimized for large sizes)

### Number Styles
- **Proportional**: Variable width (default for text)
- **Tabular**: Fixed width (for tables, timers)
- **Monospaced**: Fixed width, aligned vertically

## Usage Guidelines
1. Use system text styles (Dynamic Type)
2. Never hardcode font sizes
3. Support user's text size preferences
4. Test with accessibility sizes
5. Use SF Pro for UI, New York for editorial
6. Maintain 4.5:1 contrast for body text
7. Line height: automatic (system-defined)

## Accessibility
- Support Dynamic Type (all 12 sizes)
- Bold Text mode support
- Minimum size: 11pt (preferably 13pt+)
- Avoid light weights for small text
- Test with VoiceOver

