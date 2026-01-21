# Chess Components

Reusable Vue 3 components for Chess.com prototypes.

## Installation

```bash
npm install github:macakuaya/ChessComponents
```

## Packages

### Board Animations
Square-level visual effects for the chess board.

```javascript
import { SkillHighlight, BrilliantHighlight, ExplosionEffect } from '@chess/components/board-animations'
```

| Component | Description |
|-----------|-------------|
| `SkillHighlight` | Gold overlay + star icon + label bubble → coin fall |
| `BrilliantHighlight` | Teal overlay + exclamation icon + label |
| `ExplosionEffect` | Semicircle burst at board edge |

### Celebrations
Full-screen overlays and modals for achievements.

```javascript
import { BoardCelebration, SkillEarned, SkillUnlockedModal } from '@chess/components/celebrations'
```

| Component | Description |
|-----------|-------------|
| `BoardCelebration` | Overlay with image, title, subtitle |
| `SkillEarned` | Progress bar with animated slot-machine counter |
| `SkillUnlockedModal` | Hero modal for skill mastery |

### Sounds
Audio utilities for chess game sounds.

```javascript
import { useSound } from '@chess/components/sounds'
```

| Export | Description |
|--------|-------------|
| `useSound()` | Composable to play chess sounds from CDN |

## Usage Example

```vue
<script setup>
import { BoardCelebration, SkillEarned } from '@chess/components/celebrations'
import { useSound } from '@chess/components/sounds'

const { playSound } = useSound()
</script>

<template>
  <BoardCelebration
    :visible="showCelebration"
    title="You Earned a Skill Point!"
    subtitle="Keep reviewing until you master every skill"
  />
</template>
```

## Requirements

- Vue 3.x
- Optional: `@chesscom/design-system` (for CcIcon in BrilliantHighlight)
