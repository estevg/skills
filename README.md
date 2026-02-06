# React Native Reanimated Animations Skill

> Agent Skills–compliant skill for React Native Reanimated. Expert guidance for animations: transitions, gestures, scroll-linked effects, layout animations, CSS animations (v4), shared element transitions, worklets, and real-world component patterns.

[![Agent Skills](https://img.shields.io/badge/Agent_Skills-Compatible-blue)](https://agentskills.io)
[![Claude Code Plugin](https://img.shields.io/badge/Claude_Code-Plugin-blue)](https://code.claude.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## What is this?

This skill provides comprehensive guidance for creating performant animations in React Native using Reanimated, including:

- ✅ **SKILL.md** – Core patterns, animation selection, quick snippets, version detection (v3/v4)
- ✅ **8 reference docs** – API reference, gesture patterns, layout animations, CSS animations, shared element transitions, component patterns, worklets & advanced APIs, testing & properties
- ✅ **Version support** – Both Reanimated v3 (Legacy + New Architecture) and v4 (New Architecture only)
- ✅ **Real-world patterns** – Accordion, bottom sheet, flip card, parallax, FAB, collapsing header

## Installation

### Using npx skills

```bash
# Install from GitHub
npx skills add estevg/skills --skill creating-reanimated-animations

# Or with full URL
npx skills add https://github.com/estevg/skills --skill creating-reanimated-animations
```

The skill directory is **creating-reanimated-animations** (Agent Skills spec: name matches folder).

### Using Claude Code Plugin

```bash
# Add the marketplace
/plugin marketplace add estevg/skills

# Install the plugin
/plugin install creating-reanimated-animations@esteban-skills
```

### Manual Installation (Cursor)

1. Clone or download this repository
2. Copy the **creating-reanimated-animations** folder to one of these locations:
   - `~/.cursor/skills/creating-reanimated-animations/` (global)
   - `.cursor/skills/creating-reanimated-animations/` (project-specific)

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
├── SKILL.md                          # Main skill with core patterns
└── references/
    ├── api-reference.md              # Full hook signatures, v3↔v4 differences
    ├── gesture-patterns.md           # Drag, pinch, fling integrations
    ├── layout-animations.md          # Entering/exiting, layout transitions
    ├── css-animations-detailed.md    # CSS animations (v4 only)
    ├── shared-element-transitions.md # Screen-to-screen animations
    ├── component-patterns.md         # Accordion, bottom sheet, flip card, FAB
    ├── worklets-advanced.md          # Worklets, runOnJS/runOnUI
    └── testing-and-properties.md     # Jest testing, animatable properties
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
  // 1. Create shared value (lives on UI thread)
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
| Clamp spring range      | `withClamp({min, max}, withSpring(to))`      | v4: limits overshoot   |
| Loop/pulse/shake        | `withRepeat(anim, reps, reverse)`            | `reps=0` for infinite  |
| Multi-step choreography | `withSequence(anim1, anim2, ...)`            | Runs in order          |

## Requirements

Works with any Agent Skills-compatible tool:

- ✅ Claude Code
- ✅ Claude Desktop (with skills enabled)
- ✅ OpenAI Codex CLI
- ✅ Cursor (via skills)
- ✅ Any tool supporting the Agent Skills format

### Project Requirements

- React Native with Reanimated v3 or v4
- `react-native-gesture-handler` (for gesture patterns)
- `react-native-worklets` (for Reanimated v4)

## Features

### 🎯 Intelligent Activation

The skill knows when to activate based on context - no need to manually invoke it.

### 📚 Progressive Disclosure

Information is loaded on-demand to keep context efficient:

1. Metadata always available
2. Main docs when skill activates
3. Detailed references as needed

### ✨ Version-Aware

Automatically detects and adapts to your Reanimated version:

- **v4** (New Architecture only): requires `react-native-worklets`
- **v3** (supports Legacy and New Architecture): single package

### 🔄 Up-to-date Patterns

Based on React Native Reanimated documentation:

- Layout animations (entering/exiting)
- CSS animations & transitions (v4)
- Shared element transitions
- Gesture handler integration

## Contributing

Issues and PRs welcome at [github.com/estevg/skills](https://github.com/estevg/skills)

1. Check existing issues first
2. Open a new issue with details
3. Or submit a PR with fixes/improvements

## Related Resources

- [React Native Reanimated Docs](https://docs.swmansion.com/react-native-reanimated/)
- [React Native Gesture Handler](https://docs.swmansion.com/react-native-gesture-handler/)
- [Agent Skills Specification](https://agentskills.io)
- [Agent Skills Examples](https://github.com/anthropics/skills)
- [Skills Marketplace](https://skillsmp.com)

## License

MIT - See [LICENSE](LICENSE) file for details.

## Star History

If you find this skill useful, please consider giving it a ⭐ on GitHub!

---

**Made with ❤️ for the React Native community**
