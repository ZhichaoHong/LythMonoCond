<h1 align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono-title-dark-mode.svg?raw=true">
    <source media="(prefers-color-scheme: light)" srcset="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono-title-light-mode.svg?raw=true">
    <img alt="Lyth Mono" src="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono-title-light-mode.svg?raw=true">
  </picture>
</h1>

> **Lyth Mono Cond** is a condensed fork of [Lyth Mono](https://github.com/why-trv/LythMono). It uses the same glyph designs and vertical metrics, with a 500-unit character width (upstream: 604). See [Condensed Width](#condensed-width) for details. The rest of this README comes from upstream, with names and commands updated for this fork. Screenshots show upstream Lyth Mono at its Normal width.

**Lyth Mono** is an attempt at my 'dream' programming font. Technically, it's a custom build of [Iosevka](https://github.com/be5invis/Iosevka) with metric overrides and an opinionated selection of glyphs.

<img src="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono.png?raw=true" alt="Lyth Mono sample" width="830"/>

## Why?

I have a soft spot for industrial neo-grotesque designs like DIN, but, to my surprise, I haven't seen many coding fonts in this style and none that would tick all the boxes for me.

In a nutshell:
- somewhat square-ish, but not too much,
- simple shapes, minimal usage of tails and serifs, but not too geometric-y,
- decently legible at 12–13 pt,
- all the usual programming font concerns like `O08`, `iIl1` etc.

There are a couple of notable fonts that caught my attention in recent years, namely [**JetBrains Mono**](https://github.com/JetBrains/JetBrainsMono) and [**Berkeley Mono**](https://usgraphics.com/products/berkeley-mono) (as well as its Iosevka-based lookalike, [**Ioskeley Mono**](https://github.com/ahatem/IoskeleyMono)). Those are gorgeous fonts, but still I've managed to find my gripes with them:
- JetBrains Mono is very legible and functional, but I wish it was less condensed and geometric-y.
- Berkeley Mono looks cool, especially in the larger sizes it's presented at, but I feel legibility is compromised at smaller sizes — all characters begin looking like squares.

Here is an animated GIF comparing **Lyth Mono** to **Ioskeley Mono** and **JetBrains Mono**:

<img src="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-ioskeley-jetbrains-mono.gif?raw=true" alt="Lyth Mono vs Ioskeley Mono vs JetBrains Mono" width="830"/>

## Preview

Lyth Mono is available at [**programmingfonts.org**](https://www.programmingfonts.org/#lyth-mono) for a quick test drive alongside your current favorite font.

And here's a screenshot of Lyth Mono in action in VS Code:

[<img src="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono-vscode.png?raw=true" alt="Lyth Mono vs Ioskeley Mono vs JetBrains Mono" width="830"/>](https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono-vscode.png?raw=true)

## Variations

### Term

Lyth Mono comes in `normal` (no postfix) and `term` (Term) versions. The latter has narrow arrows and geometric symbols for use in terminal emulators.

### Condensed Width

This fork builds a single narrow width: 500 units, the same as Iosevka and PragmataPro, against upstream Lyth Mono's 604. That fits about 21% more characters on a line. Vertical metrics match upstream.

Two changes get there:
- Letters are narrower: the body of `n` is 366 units against upstream's ~424, close to Iosevka's 372 and PragmataPro's 363.
- Side bearings tighten from 90 to 67 units at Regular (78 to 58 at Bold), in line with Iosevka (64) and PragmataPro (68).

The families are named `Lyth Mono Cond`, `Lyth Mono Cond Term`, `Lyth Mono Cond Square` and so on, so they install side by side with upstream Lyth Mono. Font files follow the plan names, e.g. `LythMonoCond-Regular.ttf`. The narrower width is baked into the family, so the fonts declare the standard width class and need no `font-stretch` setting.

### Square / Round

In addition to the default configuration, there are extra Square and Round versions that modify the arc curvature to appear more 'squared' or 'rounded'. This is mostly apparent with characters like `o`, `c`, `e` etc. The difference is rather subtle and, since proportions are otherwise the same, may be more of a 'feel' than a 'look' thing.

<img src="https://github.com/why-trv/LythMono/blob/assets/assets/lyth-mono-normal-round-square.gif?raw=true" alt="Lyth Mono vs Lyth Mono Round vs Lyth Mono Square" width="830"/>

### Nerd Fonts

This repository provides both 'vanilla' and [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)–patched versions of the fonts.

Caveats:
- The patcher PascalCases the original font family names, e.g. `LythMonoCondTermRound Nerd Font` instead of `Lyth Mono Cond Term Round`.
- The patcher messes with leading (line height) in some way, so you may need to adjust it in your terminal emulator.

## Installation

1. Head over to [**Releases**](../../releases).
2. Find the latest release and download the `.zip` file for the desired font variation, e.g. `LythMonoCond.zip`.
3. Unzip the archive and install the font files on your OS.

## Building

If you want to tweak the font configurations (aka build plans) in some way (e.g. pick other glyph variants or adjust the metrics), there's a couple of ways to do it.

### Building with GitHub Actions

1. [**Fork**](../../fork) this repository.
2. Make desired changes to the build plans in the `/plans` directory.
3. Commit and push your changes. A push to the `main` branch will run a workflow to build the fonts.
4. Head over to [**Actions**](../../actions), wait for the workflow to complete and find the built fonts archive in the **Artifacts** section.

The downside is, since it builds all font formats and variants (normal / square / round, hinted / unhinted etc.) and patches all of them with Nerd Fonts, it takes 30+ minutes to complete.

### Building from Source Locally

#### Prerequisites

Iosevka requires [**Node.js**](https://nodejs.org/en/download) 20+ and [**ttfautohint**](https://freetype.org/ttfautohint/#download) to build. The former provides a bunch of options to choose from on its website, while for the latter the easiest way is likely to use a package manager of your choice (e.g. `brew install ttfautohint` on macOS).
I guess you don't need `ttfautohint` if you're going to build only unhinted versions of the fonts.

#### TL;DR

```
git clone --recursive --shallow-submodules https://github.com/ZhichaoHong/LythMonoCond.git
npm install
npm run build
```

The built fonts will be in `dist/`.

If you want Nerd Font icons, run this after the build:
```
npm run patch-nerdfonts
```

On macOS and Linux you can also run
```
npm run install-fonts
```
to automatically install TTFs to the user fonts directory.

#### Parametrized Build

##### 1. Clone this Repository

```
git clone --recursive --shallow-submodules https://github.com/ZhichaoHong/LythMonoCond.git
```

Iosevka's full git history is very heavy (tens of GB), so it's strongly recommended to do a shallow clone of the Iosevka submodule (`--shallow-submodules`).

##### 2. Install Dependencies

```
npm install
```

##### 3. Build

```
npm run build [-- [format | target...] [--ts [--keep-old]]]
```
- `format` is the font format option to be forwarded to the Iosevka build system:
    - `contents` (all formats, default)
    - `ttf` (TTF, hinted + unhinted)
    - `ttf-unhinted` (TTF, unhinted)
    - `webfont` (CSS + WOFF2)
    - `webfont-unhinted`
    - `woff2` (WOFF2 only)
    - `woff2-unhinted`
- `target...` - space-separated pairs of format and font build plan names, e.g. `contents::LythMonoCond ttf::LythMonoCondTerm`.

Use the latter to specify specific fonts (build plans) to build. Otherwise, if only `format`, or neither `format` nor `target...` is specified, the script will build all plans in the `plans/` directory.

- `--ts` automatically appends a timestamp to the font family name (and consequently, the directory and font file names). This can be handy when iterating on a design to bypass font cache issues on macOS, or just to keep multiple iterations installed (see `--keep-old`).
- `--keep-old` prevents the build script from automatically removing older timestamped versions of the font.

When the build finishes, font files will be available in `dist/` (symlinked to `Iosevka/dist/`)

###### Examples:
```
npm run build -- ttf --ts
```
builds a timestamp-versioned TTF and deletes the previously existing timestamped versions of the font.

```
npm run build -- contents::LythMonoCond ttf::LythMonoCondTerm
```
builds a normal (non-timestamp-versioned) `LythMonoCond` in all formats and `LythMonoCondTerm` in hinted and unhinted TTF.

##### 4. Patch Nerd Fonts (Optional)

To patch the built fonts with Nerd Font icons, run
```
npm run patch-nerdfonts [-- [--hinted] [--unhinted] [-j=N | --jobs=N]]
```

This will patch all TTF fonts in `dist/`. Patching takes quite a while, so it's recommended you don't build any font variants you aren't going to need.

If no flags are passed, the script will default to patching only the hinted versions of the fonts. If the hinted font directory is not there, it will fallback to patching the unhinted versions.

For more control, use these flags:
- `--hinted` - patch hinted versions of fonts,
- `--unhinted` - patch unhinted versions of the fonts.

Pass both flags to patch both hinted and unhinted versions.

`-j=N` or `--jobs=N` makes N font patching jobs run in parallel (default: number of CPU cores).

##### 5. Install Font Files

You can install the built font files manually, or, for TTF, you also have the option of running this:
```
npm run install-fonts [-- [--unhinted] [--keep-old]]
```
to copy all font files from `dist/` to your user font directory (`~/Library/Fonts` on macOS, `~/.local/share/fonts` on Linux).

Options:
- `--unhinted` - copy the unhinted version of the fonts, otherwise defaults to hinted.
- `--keep-old` - for timestamped builds, don't delete existing timestamped files.
- `--clipboard` - copy family names to clipboard for recall via clipboard manager (macOS only, requires `fontconfig`, which should be already installed as a dependency of `ttfautohint`).

#### (Cleanup)

```
npm run clean
```
will delete the `dist/` symlink and `Iosevka/dist/` where the built font files are located.

### Build Customization

You can tweak and add font configurations by modifying `.toml` files in `plans/`.

In general, please refer to Iosevka's [Customized Build](https://github.com/be5invis/Iosevka/blob/main/doc/custom-build.md#customized-build) section for details on available parameters, since the Lyth Mono build system is working on top of Iosevka's.

However, keep in mind the differences between Lyth Mono and vanilla Iosevka build systems. In Lyth Mono:
- Any single file in `plans/` defines one and only one build plan.
- `buildPlan.<plan-name>` prefixes are omitted and the plan name is derived from the file name.
- You should be able to use `inherits` keys of vanilla Iosevka where it allows, but this is somewhat limiting and verbose, so instead of defining the whole plan, you can define a base build plan (e.g. `basePlan = "LythMonoCond"`) and the keys to override (see `LythMonoCondTerm.toml` for example).

The build script processes and gathers all build plans in `Iosevka/private-build-plans.toml` and hands it off to Iosevka to build.
