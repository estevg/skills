# React Native Reanimated Animations Skill

> Claude Code plugin for generating performant React Native Reanimated animation code (v3 & v4). Expert guidance for transitions, gestures, scroll-linked effects, layout animations, CSS animations, shared element transitions, and more.

[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-blue)](https://code.claude.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## What is this?

This skill provides comprehensive guidance for creating performant animations in React Native using Reanimated, including:

- ✅ **SKILL.md** – Core patterns, animation selection, quick snippets
- ✅ **8 reference docs** – API reference, gesture patterns, layout animations, CSS animations, shared element transitions, component patterns, worklets & advanced APIs, testing & properties
- ✅ **Version support** – Both Reanimated v3 and v4 (New Architecture)
- ✅ **Real-world patterns** – Accordion, bottom sheet, flip card, parallax, FAB

## Installation

### Using Claude Code

```bash
# Add the marketplace
/plugin marketplace add estevg/skills

# Install the plugin
/plugin install creating-reanimated-animations@esteban-skills
```

### Verify Installation

```bash
# List installed plugins
/plugin list
```

## Usage

Once installed, the skill automatically activates when you:

- Ask about React Native animations
- Mention "reanimated", "animations", or "gestures"
- Request help with transitions, spring animations, or layout effects
- Need to implement scroll-linked animations or shared element transitions

### Example Queries

**Creating Animations:**

```
"Create a fade in animation with spring effect"
"Implement a parallax scroll header"
"Build a swipeable card with gesture handler"
```

**Layout Animations:**

```
"Add entering/exiting animations to a list"
"Create a layout transition for reordering items"
"Implement a keyframe animation for a loading indicator"
```

**Advanced Patterns:**

```
"Build an accordion component with smooth animations"
"Create a bottom sheet with gesture controls"
"Implement shared element transitions between screens"
```

## What's Included

### Skill Structure

```
creating-reanimated-animations/
├── SKILL.md                    # Main skill file with core patterns
└── references/
    ├── api-reference.md        # Full hook signatures, v3↔v4 differences
    ├── gesture-patterns.md     # Drag, pinch, fling integrations
    ├── layout-animations.md    # Entering/exiting, layout transitions
    ├── css-animations-detailed.md  # CSS animations (v4 only)
    ├── shared-element-transitions.md
    ├── component-patterns.md   # Accordion, bottom sheet, flip card, FAB
    ├── worklets-advanced.md    # Worklets, runOnJS/runOnUI
    └── testing-and-properties.md
```

### Core Pattern

Every animation follows three steps:

```tsx
import Animated, {
  useSharedValue,
  useAnimatedStyle,
  withTiming,
} from "react-native-reanimated";

function Component() {
  // 1. Create shared value
  const offset = useSharedValue(0);

  // 2. Bind to style
  const animatedStyle = useAnimatedStyle(() => ({
    transform: [{ translateX: offset.value }],
  }));

  // 3. Trigger animation
  const handlePress = () => {
    offset.value = withTiming(200, { duration: 500 });
  };

  return <Animated.View style={[styles.box, animatedStyle]} />;
}
```

### Animation Selection

| User wants              | Function                                     | Key params             |
| ----------------------- | -------------------------------------------- | ---------------------- |
| Smooth fixed-duration   | `withTiming(to, {duration, easing})`         | Default: 300ms         |
| Natural bouncy feel     | `withSpring(to, {mass, damping, stiffness})` | Default: mass=1        |
| Momentum after fling    | `withDecay({velocity, clamp})`               | Needs initial velocity |
| Loop/pulse/shake        | `withRepeat(anim, reps, reverse)`            | `reps=0` for infinite  |
| Multi-step choreography | `withSequence(anim1, anim2, ...)`            | Runs in order          |

## Requirements

Works with:

- ✅ Claude Code
- ✅ Any Claude Code plugin-compatible environment

### Project Requirements

- React Native with Reanimated v3 or v4
- `react-native-gesture-handler` (for gesture patterns)

## Contributing

Issues and PRs welcome at [github.com/estevg/skills](https://github.com/estevg/skills)

## Related Resources

- [React Native Reanimated Docs](https://docs.swmansion.com/react-native-reanimated/)
- [React Native Gesture Handler](https://docs.swmansion.com/react-native-gesture-handler/)
- [Claude Code Plugins](https://code.claude.com)

## License

MIT - See [LICENSE](LICENSE) file for details.

---

**Made with ❤️ for the React Native community**
