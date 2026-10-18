## Level 14: Hanuman Travels to Lanka 🌊

### Game concept

**Genre:** High-mobility platformer and aerial traversal.

### Contextual actions

- Control Hanuman.
- Reach the ocean cliff.
- Build momentum.
- Perform a powerful leap.
- Travel across floating platforms, islands, and aerial obstacles.
- Land on the island of Lanka.

### Characters

- Hanuman
- Optional ocean creatures
- Lanka guards encountered near the landing area

### Powers

- Powerful leap
- Extended aerial movement
- Midair steering
- Controlled landing

### Environment

An expansive ocean with islands, clouds, distant mountains, and Lanka on the horizon.

### Rooms or stages

- Mountain launch point
- Ocean traversal
- Floating-rock section
- Cloud section
- Lanka landing zone

### Tilemap

Use terrain tiles for the mountain and landing areas. Use modular floating platforms and invisible boundaries for the ocean traversal.

### Physics

- Gravity
- Jump velocity
- Air control
- Drag
- Collision detection

### Mathematics

- Projectile motion
- Vector magnitude
- Travel distance
- Landing prediction
- Parallax camera movement

For idealized projectile motion:

$$
T=\frac{2v_0\sin\theta}{g}
$$

$$
R=\frac{v_0^2\sin(2\theta)}{g}
$$

These equations provide an initial estimate of flight time and horizontal range for a launch from and landing at the same height. Real game movement may use additional air-control forces.

### Animation

- Hanuman's crouching launch pose
- Powerful leap
- Midair body rotation
- Tail movement
- Landing impact
- Cloud and water movement

### Audio

- Wind
- Powerful launch effect
- Air rush
- Ocean waves
- Landing impact
- Expansive orchestral music

### Prototype objective

Cross the ocean and reach Lanka.

**Success condition:** Unlock the Lanka exploration level.

---
