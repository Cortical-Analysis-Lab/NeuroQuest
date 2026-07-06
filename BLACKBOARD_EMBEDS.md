# Blackboard Embed HTML

Use these snippets in Blackboard's HTML/source editor or embed tool.

Base site URL:

```text
https://cortical-analysis-lab.github.io/NeuroQuest/
```

## Current Modules

### Neuroscience vs Psychology

```html
<iframe
  title="NeuroQuest Neuroscience vs Psychology"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=neuropsych"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

### Tools & Techniques

```html
<iframe
  title="NeuroQuest Tools and Techniques"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=tools"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

### Anatomy & Function of the Nervous System

```html
<iframe
  title="NeuroQuest Anatomy"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=anatomy"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

### Neurophysiology & Communication

```html
<iframe
  title="NeuroQuest Neurophysiology"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=neurophysiology"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

### Aging

```html
<iframe
  title="NeuroQuest Aging"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=aging"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

### Language and Communication

```html
<iframe
  title="NeuroQuest Language and Communication"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=language"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

### Technology and the Brain

```html
<iframe
  title="NeuroQuest Technology and the Brain"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=technology"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

## Future Module Template

Add the module ID to `index.html`'s `openModule()` alias map, then use this pattern.

```html
<iframe
  title="NeuroQuest MODULE TITLE"
  src="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=MODULE_ID"
  width="100%"
  height="850"
  style="border:0; width:100%; min-height:850px;"
  allow="autoplay; fullscreen">
</iframe>
```

## Fallback Link

If Blackboard strips or blocks iframe embeds, use a normal link instead.

```html
<a href="https://cortical-analysis-lab.github.io/NeuroQuest/index.html?module=MODULE_ID" target="_blank" rel="noopener">
  Open NeuroQuest MODULE TITLE
</a>
```
