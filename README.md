# 🎮 PongGame  

**Neon Pong Extreme** is an enhanced Pygame implementation of the classic Pong game, featuring:
- Neon lighting effects  
- Dynamic backgrounds and particles  
- Rainbow mode and screen shake  
- Score tracking and UI animation

---

## 🔧 Constants

| Constant         | Description                                     |
|------------------|-------------------------------------------------|
| `SCREEN_WIDTH`   | Width of the game screen (in pixels)            |
| `SCREEN_HEIGHT`  | Height of the game screen                       |
| `PADDLE_WIDTH`   | Width of the paddles                            |
| `PADDLE_HEIGHT`  | Height of the paddles                           |
| `BALL_SIZE`      | Diameter of the ball                            |
| `PADDLE_SPEED`   | Movement speed of paddles                       |
| `BALL_SPEED`     | Base speed of the ball                          |
| `COLORS`         | Dictionary of vibrant neon RGB color values     |

---

## 🌌 `AnimatedBackground`

Manages the animated starfield and glowing grid.

### Methods

- `__init__()`: Initializes stars and gridlines.
- `create_stars()`: Populates stars with random positions and twinkle attributes.
- `create_grid()`: Defines vertical and horizontal gridlines.
- `update()`: Animates star brightness and grid shimmer.
- `draw(screen)`: Renders the animated stars and grid.

---

## 🧱 `Paddle`

Represents a player-controlled paddle.

### Attributes

- `rect`: The `pygame.Rect` of the paddle.
- `speed`: Movement speed.
- `is_ai`: Boolean indicating AI control.
- `up_key`, `down_key`: Control key mappings.

### Methods

- `move(ball=None)`: Updates paddle position based on user input or AI behavior.
- `draw(screen, color)`: Renders the paddle with motion blur effect.

---

## 🟠 `Ball`

Handles the ball’s behavior and rendering.

### Attributes

- `rect`: The ball’s `pygame.Rect`.
- `velocity`: Tuple of `(x, y)` speed.
- `trail`: List of past ball positions (for trail effect).
- `rainbow`: If True, enables color-shifting.
- `color_offset`: Angle for hue shift in rainbow mode.

### Methods

- `reset()`: Re-centers ball and randomizes velocity.
- `update()`: Moves ball and updates the trail.
- `draw(screen, color)`: Draws the ball and trailing glow.

---

## 💥 `Particle`

A single visual particle, used for collision or score effects.

### Attributes

- `x`, `y`: Position  
- `vx`, `vy`: Velocity vector  
- `size`: Size of the particle  
- `color`: Neon-style RGB color  
- `lifespan`: Remaining lifetime (in frames)

### Methods

- `update()`: Moves and fades the particle.
- `draw(screen)`: Renders the particle with glow.

---

## 🌟 `ParticleSystem`

Controls all on-screen particles.

### Methods

- `emit(x, y, color)`: Spawns a group of particles at position `(x, y)`.
- `update_and_draw(screen)`: Updates all particles and draws them.

---

## 📺 `UIManager`

Handles score display, game text, and game state animations.

### Attributes

- `font`, `large_font`: Pygame fonts
- `score_left`, `score_right`: Player scores
- `messages`: Queue of messages to show

### Methods

- `draw_score(screen)`: Displays scores at the top of the screen.
- `draw_message(screen, text, scale, color)`: Shows a temporary animated message.

---

## 🌈 `ColorUtils`

Helper for rainbow hue shifting.

### Methods

- `rainbow_color(offset, brightness=255)`: Returns a cycling RGB color based on an angle offset.

---

## 🕹️ `Game`

Main game logic, containing the game loop, collision, and state management.

### Attributes

- `screen`: Pygame screen object
- `clock`: Controls game framerate
- `paddle_left`, `paddle_right`: Player paddles
- `ball`: Ball object
- `bg`: AnimatedBackground object
- `particles`: ParticleSystem object
- `ui`: UIManager object
- `shake_timer`: Controls screen shake effect
- `rainbow_mode`: Toggles rainbow color mode

### Methods

- `__init__()`: Initializes all components and state
- `run()`: Game loop – handles input, update, and draw calls
- `handle_collisions()`: Detects and processes ball collisions
- `trigger_score(player)`: Handles scoring logic, UI, and particles
- `screen_shake()`: Offsets the screen temporarily for a shaking effect

---

## 💡 Special Features

| Feature          | Description |
|------------------|-------------|
| Rainbow Mode     | Cycles ball color through hues automatically |
| Screen Shake     | Triggered on scoring to enhance feedback |
| Particle Effects | Triggered on collision or point events |
| Energy Trail     | Ball leaves a glowing motion trail |
| Glowing UI       | Scores and messages pulse with animation |

---

## 🔁 Game Flow

1. Initialize game and objects  
2. Enter loop:
   - Handle input  
   - Update objects (ball, paddles, background, particles)  
   - Detect collisions  
   - Update UI and score  
   - Render everything  
3. Repeat until quit

---
