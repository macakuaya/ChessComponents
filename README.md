# Chess Components

Reusable Vue 3 components for Chess.com prototypes - animations, celebrations, and sounds.

## Installation

```bash
npm install github:macakuaya/ChessComponents
```

## Quick Start

```javascript
// Import from main entry point
import { BoardCelebration, SkillEarned, SkillUnlockedModal, playSound } from '@chess/components'

// Or import from specific modules
import { BoardCelebration } from '@chess/components/celebrations'
import { playSound } from '@chess/components/sounds'
```

---

## Celebrations

Full-screen overlays and modals for achievements and progress.

### BoardCelebration

Overlay that appears on top of the board with an image, title, and subtitle.

```vue
<BoardCelebration
  :visible="showCelebration"
  image="/path/to/image.png"
  title="You Earned a Skill Point!"
  subtitle="Keep reviewing until you master every skill"
/>
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `visible` | Boolean | `false` | Show/hide the celebration |
| `image` | String | `null` | Image URL to display |
| `title` | String | `'You Earned a Skill Point'` | Main title text |
| `subtitle` | String | `'Keep reviewing...'` | Secondary text |

### SkillEarned

Progress bar with animated slot-machine counter that slides up from the bottom.

```vue
<SkillEarned
  :visible="showSkillEarned"
  skill-name="Queen Sacrifice"
  :current="5"
  :max="10"
  icon-src="/icons/queen.png"
  @counter-complete="onAnimationDone"
/>
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `visible` | Boolean | `false` | Show/hide the component |
| `skillName` | String | `'Skewers'` | Name of the skill |
| `current` | Number | `1` | Current progress (before animation) |
| `max` | Number | `10` | Maximum progress |
| `iconSrc` | String | `null` | Full URL/path to skill icon |

| Event | Description |
|-------|-------------|
| `counter-complete` | Emitted when counter animation finishes |

### SkillUnlockedModal

Full-screen hero modal for celebrating skill mastery.

```vue
<SkillUnlockedModal
  :visible="showModal"
  skill-name="Queen Sacrifice"
  skill-description="A tactical move where you deliberately give up your queen..."
  skill-image="/path/to/hero-image.png"
  :show-share-button="true"
  @close="handleClose"
  @continue="handleContinue"
  @share="handleShare"
/>
```

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `visible` | Boolean | `false` | Show/hide the modal |
| `skillName` | String | `'Queen Sacrifice'` | Skill title |
| `skillDescription` | String | `'A tactical move...'` | Skill description |
| `skillImage` | String | `''` | Hero image URL |
| `showShareButton` | Boolean | `false` | Show Share + Continue buttons |

| Event | Description |
|-------|-------------|
| `close` | User clicked close button |
| `continue` | User clicked Continue |
| `share` | User clicked Share |

**Note:** Requires `@chesscom/design-system` for CcButton and CcIcon.

---

## Sounds

Audio utilities for playing chess game sounds from the Chess.com CDN.

### playSound

```javascript
import { playSound } from '@chess/components'

// Play a sound
playSound('move')     // Normal move
playSound('capture')  // Piece captured
playSound('check')    // Check or checkmate
playSound('castle')   // Castling
playSound('promote')  // Pawn promotion
```

### useSound (Composable)

```javascript
import { useSound } from '@chess/components'

const { playSound, soundTypes } = useSound()

// soundTypes = ['move', 'capture', 'castle', 'check', 'promote']
```

---

## Board Animations

CSS animation timings and colors for board-level effects (skill highlights, brilliant moves).

```javascript
import { ANIMATION_TIMINGS, ANIMATION_COLORS } from '@chess/components'

// Timings (in ms)
ANIMATION_TIMINGS.skillTotalDuration  // 1350ms - full skill animation
ANIMATION_TIMINGS.skillCoinFall       // 500ms - coin falls to progress bar
ANIMATION_TIMINGS.brilliantTotalDuration // 800ms - full brilliant animation

// Colors
ANIMATION_COLORS.skillHighlight    // '#E3AA24' (gold)
ANIMATION_COLORS.brilliantHighlight // '#26C2A3' (teal)
```

---

## Requirements

- Vue 3.x (peer dependency)
- Optional: `@chesscom/design-system` (required for SkillUnlockedModal)

## Project Structure

```
src/
├── index.js                 # Main entry point
├── celebrations/
│   ├── BoardCelebration.vue
│   ├── SkillEarned.vue
│   └── SkillUnlockedModal.vue
├── sounds/
│   └── useSound.js
└── board-animations/
    └── index.js             # Animation constants
```

## License

MIT
