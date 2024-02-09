---
type: NoteCard
tags: []
---

# IU DS Tokens
Each design system is based on a well-defined specification of color, space, size, font, typography, shadow, etc, which we call **design tokens**.

Design tokens are then used to design all the components of a design system.

## Tools to create design systems

Tools like stitches allow us to create design tokens and then use them to create components. Here is an example

```js
export const { styled, theme, css, createTheme, globalCss, keyframes } =
  createStitches({
    theme: {
      colors: {
        ...tokens.light,
        ...tokens.staticColors,
        ...tokens.defaultTheme,
      },
      sizes: tokens.sizes,
      space: tokens.spaces,
      radii: tokens.radii,
      fonts: tokens.fonts,
      fontSizes: tokens.fontSizes,
      fontWeights: tokens.fontWeights,
      shadows: tokens.shadows,
      zIndices: tokens.zIndices,
      lineHeights: {
        ...tokens.lineHeights,
        headline: '$110',
        body: '$160',
        meta: '$125',
        subhead: '$meta',
      },
      transitions: {
        allFast: 'all $fast $inOut',
        fast: '0.2s',
        normal: '0.3s',
        inOut: 'cubic-bezier(.4, 0, .2, 1)',
      },
      borderStyles: {},
      borderWidths: {},
      letterSpacings: {},
    },
    media: {
      sm: '(max-width: 767px)',
      md: '(min-width: 768px) and (max-width: 899px)',
      lg: '(min-width: 900px) and (max-width: 1023px)',
      xl: '(min-width: 1024px) and (max-width: 1279px)',
      xxl: '(min-width: 1280px) and (max-width: 1440px)',
      notSm: '(min-width: 768px)',
      notMd: '(min-width: 900px)',
      notLg: '(min-width: 1024px)',
      notXl: '(min-width: 1280px)',
      notXxl: '(min-width: 1441px)',
      motion: '(prefers-reduced-motion)',
      hover: '(any-hover: hover)',
      dark: '(prefers-color-scheme: dark)',
      light: '(prefers-color-scheme: light)',
    },
    utils: {
      // margin
      m: (value) => ({
        margin: value,
      }),
      mt: (value) => ({
        marginTop: value,
      }),
      mr: (value) => ({
        marginRight: value,
      }),
      mb: (value) => ({
        marginBottom: value,
      }),
      ml: (value) => ({
        marginLeft: value,
      }),
      mx: (value) => ({
        marginLeft: value,
        marginRight: value,
      }),
      my: (value) => ({
        marginTop: value,
        marginBottom: value,
      }),
      p: (value) => ({
        padding: value,
      }),
      pt: (value) => ({
        paddingTop: value,
      }),
      pr: (value) => ({
        paddingRight: value,
      }),
      pb: (value) => ({
        paddingBottom: value,
      }),
      pl: (value) => ({
        paddingLeft: value,
      }),
      px: (value) => ({
        paddingLeft: value,
        paddingRight: value,
      }),
      py: (value) => ({
        paddingTop: value,
        paddingBottom: value,
      }),

      size: (value) => ({
        width: value?.[0],
        height: value?.[1],
      }),
      linearGradient: (value) => ({
        backgroundImage: `linear-gradient(${value})`,
      }),
      br: (value) => ({
        borderRadius: value,
      }),
      bg: (value) => ({
        background: value,
      }),
      bs: (value) => ({
        boxShadow: value,
      }),
      align: (value) => ({
        alignItems: value,
      }),
      justify: (value) => ({
        justifyContent: value,
      }),
    },
  });
```

## Learn more

<https://designsystem.digital.gov/design-tokens/>