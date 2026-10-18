## Level 19: Rama Defeats Ravana

### Game concept

**Genre:** Multi-phase boss battle.

### Contextual actions

- Enter the final battlefield.
- Learn Ravana's attack patterns.
- Dodge sword attacks.
- Avoid magical projectiles.
- Find openings for counterattacks.
- Use precision archery.
- Complete the final story-triggered attack.

### Characters

- Rama
- Ravana
- Optional allied characters appearing in cinematic sequences

### Powers

- Precision shot
- Defensive focus
- Charged arrow
- Final story-specific ability

### Environment

A dramatic battlefield with Lanka's towers in the distance, swirling clouds, and a wide arena.

### Arena layout

Use a flat central combat area with:

- Left and right boundaries
- Two or three optional platforms
- Clearly visible hazard zones
- A central boss arena

### Tilemap

Use modular stone ground tiles, broken pillars, and decorative background ruins.

Keep decorative objects out of critical combat areas.

### Physics

- Boss collision
- Projectile movement
- Dodge movement
- Knockback
- Hit detection
- Temporary invulnerability
- Arena boundaries

### Mathematics

- Boss health
- Attack timing
- Collision detection
- Projectile trajectories
- Phase transitions

Example boss state logic:

```
if health > 70%:
    phase = "sword_attacks"
elif health > 35%:
    phase = "ranged_attacks"
else:
    phase = "final_phase"
```

This is a prototype combat design, not a claim about the epic's precise sequence of attacks.

### Suggested boss phases

1. **Warrior phase:** Ravana uses measured sword attacks.
2. **Power phase:** Ravana combines melee attacks with ranged projectiles.
3. **Final phase:** The arena becomes more dangerous, and the player must identify an opening for Rama's decisive attack.

### Animation

- Ravana's idle stance
- Sword attack
- Magical attack
- Hit reaction
- Phase-transition animation
- Rama's precision aim
- Final arrow cinematic

### Audio

- Deep orchestral music
- Sword swings
- Magical projectile sounds
- Heavy impacts
- Boss warning cues
- Final arrow release
- Music resolving after victory

### Prototype objective

Defeat Ravana by learning his attack patterns and using precise timing.

**Success condition:** Complete the final battle and trigger the resolution cinematic.

---
