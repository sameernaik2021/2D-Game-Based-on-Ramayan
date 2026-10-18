# 🎮 RAMAYANA: THE EPIC JOURNEY

## Complete 2D Game Design Document — 20 Story Events

**Game concept:** A story-driven 2D action-adventure game based on the 20 major events of the Ramayana.

The player experiences the story through exploration, archery, puzzles, platforming, character interactions, boss battles, and cinematic storytelling. Each of the 20 events becomes a playable level or story chapter.

The design is suitable for a prototype built in **Unity 2D or Godot**, with vector-style characters, 2D skeletal animation, tilemaps, grid-based environments, physics, sound effects, and background music.

The game should respectfully represent the Ramayana's religious and cultural significance while making its story accessible through interactive gameplay.

---

# 1\. Overall Game Concept

### Game title

**Ramayana: The Epic Journey**

### Game genre

- 2D action-adventure
- Story-driven platformer
- Puzzle-solving game
- Archery combat
- Exploration and mythology
- Light RPG progression

### Target platforms

- PC: Windows, macOS, and Linux
- Mobile: Android and iOS
- Web: WebGL, where supported
- Optional: Game controllers and handheld gaming devices

### Recommended game engine

| Component | Recommended technology |
| --- | --- |
| Game engine | Unity 2D |
| Alternative engine | Godot 2D |
| Programming | C# for Unity or GDScript for Godot |
| Character art | Inkscape, Adobe Illustrator, or similar vector tools |
| Sprite animation | Unity 2D Animation or Spine |
| Tilemap design | Unity Tilemap or Godot TileMapLayer |
| Audio editing | Audacity or Reaper |
| Music production | Original Indian classical and orchestral-inspired music |
| UI design | Figma or an equivalent design tool |
| Version control | Git |

**Recommended visual style:** 2D vector art with hand-painted backgrounds, layered parallax scenery, skeletal character animation, and cinematic lighting.

Use a consistent art style across all 20 events.

---

# 2\. Core Gameplay Mechanics

The player controls different characters depending on the chapter. Rama is the primary playable character, while Hanuman, Lakshmana, and other allies become playable in selected levels.

### Main player actions

| Action | Gameplay function |
| --- | --- |
| Move left/right | Navigate the environment |
| Jump | Cross gaps and reach platforms |
| Crouch | Avoid attacks or pass under obstacles |
| Interact | Talk to characters, activate objects, and collect items |
| Aim bow | Target enemies or environmental objects |
| Shoot arrow | Defeat enemies or activate distant mechanisms |
| Block | Defend against incoming attacks |
| Dodge | Evade hazards |
| Climb | Navigate ladders, vines, and ledges |
| Sprint | Move quickly through selected sections |
| Use special power | Perform character-specific abilities |
| Solve puzzles | Progress through temples, forests, and palaces |
| Inspect objects | Discover lore and optional story details |

Controls should be customizable for keyboard, controller, and touchscreen.

### Example PC controls

- A/D: Move
- Space: Jump
- Shift: Sprint
- E: Interact
- Mouse: Aim
- Left mouse button: Shoot
- Right mouse button: Block or focus
- Q: Special ability
- Esc: Pause

For mobile, replace these inputs with a virtual joystick and contextual action buttons.

---

# 3\. Character Design and Powers

Each character should have a recognizable silhouette, distinctive animations, and abilities that support the story.

## Main characters

| Character | Role | Primary abilities | Gameplay purpose |
| --- | --- | --- | --- |
| Rama | Main hero | Archery, precision shots, defensive focus | Combat, puzzles, boss encounters |
| Sita | Central story character | Observation, interaction, courage | Exploration and story-driven sequences |
| Lakshmana | Companion and warrior | Defensive combat, rapid strikes | Companion support and combat |
| Hanuman | Playable hero in selected chapters | Long jumps, powerful leaps, strength | Traversal, rescue, and exploration |
| Bharata | Loyal brother | Leadership and diplomacy | Story interactions and kingdom sequences |
| Dasharatha | King of Ayodhya | Royal authority | Opening story and palace scenes |
| Kaikeyi | Queen of Ayodhya | Dialogue and political influence | Narrative decisions and palace scenes |
| Vishwamitra | Sage and mentor | Magical instruction and guidance | Tutorial and training |
| Sugriva | Vanara king | Leadership and combat support | Alliance and army-building sequences |
| Vali | Powerful vanara warrior | Strength and melee combat | Story encounter |
| Ravana | King of Lanka and principal antagonist | Sword combat, magic, multiple attack patterns | Final boss and major story conflict |
| Maricha | Antagonist in golden-deer form | Speed, illusion, evasive movement | Chase sequence |
| Surpanakha | Forest encounter character | Dialogue and transformation | Narrative encounter |
| Jatayu | Noble bird | Flight and aerial attacks | Rescue sequence |
| Indrajit | Ravana's warrior son | Illusions and ranged attacks | Boss encounter |
| Kumbhakarna | Powerful warrior | Heavy attacks and ground slams | Large-scale combat encounter |

### Character design principles

- Rama: Blue-toned skin, yellow or saffron garments, bow, quiver, and a clear heroic silhouette.
- Sita: Traditional garments, graceful movement, expressive facial animation, and a dignified posture.
- Lakshmana: Coordinated royal clothing, bow, and a more alert combat stance.
- Hanuman: Expressive face, tail rig, ornaments, and a powerful athletic silhouette.
- Ravana: Crown, royal armor, and a commanding silhouette. His ten heads may be represented through a stylized crown or layered head arrangement.

Use visual references from appropriate traditional artistic sources rather than mixing unrelated mythological designs.

---

# 4\. Character Powers and Progression

Abilities should unlock gradually as the player progresses through the story.

| Power | Unlocked during | Gameplay application |
| --- | --- | --- |
| Basic archery | Rama's childhood training | Shoot targets and fight enemies |
| Precision shot | Training challenge | Hit distant switches |
| Charged arrow | Vishwamitra's chapter | Break selected obstacles |
| Defensive focus | Early forest levels | Reduce damage from attacks |
| Focused aim | Golden Deer chapter | Track moving targets |
| Companion support | Hanuman meeting | Receive assistance during exploration |
| Powerful leap | Hanuman's ocean-crossing chapter | Cross long gaps |
| Aerial traversal | Hanuman's Lanka mission | Navigate rooftops and platforms |
| Strength action | Bridge-building chapter | Move large objects |
| Team coordination | Great War chapter | Coordinate companion attacks |
| Ultimate arrow | Final battle | Complete the final boss encounter |

**Important design rule:** Powers should unlock because of story progression and gameplay training, not simply because the player defeats enemies.

Divine and supernatural abilities should be represented as narrative elements of the game, with clear distinctions between story events and invented game mechanics.

---

# 5\. Global Technical Specifications

These settings provide a starting point for a 2D prototype. They can be adjusted after testing.

| Property | Recommended starting value |
| --- | --- |
| Game view | Landscape |
| Reference resolution | 1920 × 1080 |
| Internal pixel density | Vector-based or approximately 100 pixels per world unit for raster assets |
| Camera | Orthographic 2D |
| Target frame rate | 60 FPS |
| Main character height | Approximately 1.6–2.0 world units |
| Tile size | 1 × 1 world unit |
| Standard platform height | 0.5–1.0 world units |
| Basic movement speed | 4–6 world units/second |
| Jump velocity | Approximately 8–11 world units/second |
| Gravity magnitude | Approximately 20–30 world units/second² |
| Standard level duration | 5–10 minutes |
| Major boss encounter | 3–8 minutes |
| Total prototype length | Approximately 60–120 minutes |

These are initial tuning values, not fixed requirements.

For a vector-based game, do not force pixel-art limitations onto the artwork. Use smooth vector contours and high-resolution textures where appropriate.

---

# 6\. The 20 Story Events as Playable Game Levels

The following sections define the gameplay prototype for each event.

Each level includes:

- Contextual actions
- Main characters
- Powers and abilities
- Environment and background
- Tilemap and grid layout
- Physics and mathematics
- Animation and sound
- Prototype objective

## Level 1: Birth of Lord Rama 👑

### Story context

King Dasharatha rules Ayodhya. Rama is born into the royal family, beginning the central journey of the epic.

### Game concept

**Genre:** Narrative exploration and introductory palace level.

### Contextual actions

- Explore the royal palace.
- Interact with Dasharatha and palace attendants.
- Discover illustrated story objects.
- Trigger a cinematic sequence introducing the four princes.
- Complete a simple exploration objective.

### Characters

- Dasharatha
- Baby Rama
- Kaushalya
- Bharata, Lakshmana, and Shatrughna as infants
- Palace attendants

### Powers

No combat powers are required.

Introduce a story interaction system that will be used throughout the game.

### 2D vector art

Create vector illustrations of:

- Royal pillars
- Palace arches
- Decorative lamps
- Lotus patterns
- Royal cradles
- Curtains and ornaments

Use warm gold, saffron, cream, and red as the principal colors.

### Background and rooms

1. Palace exterior
2. Royal courtyard
3. Main throne hall
4. Queen's chamber
5. Celebration courtyard

### Grid-based layout

Use a 32 × 18 tile grid as a conceptual level-planning canvas. Each logical tile represents one world unit.

Divide the environment into separate rooms connected by doors or transitions.

### Physics concepts

- Collision detection
- Trigger zones
- Camera transitions
- Basic character movement

### Mathematics concepts

- Grid coordinates
- Position vectors
- Camera interpolation
- Linear interpolation for cinematic movement

### Animation

- Baby Rama breathing or gentle cradle movement
- Dasharatha's idle breathing
- Attendants walking
- Flags fluttering
- Lamps flickering
- Decorative particles drifting upward

### Audio

- Gentle flute
- Veena
- Soft bells
- Palace ambience
- Footsteps
- Door-opening sounds

### Prototype objective

Explore the palace and trigger the birth celebration sequence.

**Success condition:** The opening cinematic completes and the game unlocks Level 2.

---

## Level 2: Rama's Childhood and Education

### Game concept

**Genre:** Training platformer and skill-development level.

### Contextual actions

- Walk through a training ground.
- Practice jumping between platforms.
- Shoot stationary targets.
- Interact with a teacher.
- Complete an archery accuracy challenge.
- Learn the block and dodge mechanics.

### Characters

- Young Rama
- Young Lakshmana
- Other princes
- Teachers and palace guards

### Powers

- Basic archery
- Jumping
- Precision aiming
- Defensive movement

### Environment

A royal training ground with wooden targets, practice dummies, trees, and a palace wall.

### Rooms

- Archery range
- Martial arts courtyard
- Teacher's hall
- Garden path

### Tilemap

Create:

- Ground tiles
- Wall tiles
- Wooden platforms
- Training targets
- Collision zones
- Decorative foliage

### Physics

- Gravity
- Projectile motion
- Jump trajectories
- Collision response
- Friction and acceleration

### Mathematics

- Angles
- Distance and speed
- Coordinate geometry
- Projectile trajectory
- Accuracy error

For a simple projectile, horizontal and vertical motion can be modeled as:

$$
x(t)=x_0+v_x t
$$

$$
y(t)=y_0+v_y t-\frac{1}{2}gt^2
$$

### Animation

- Idle breathing
- Bow-drawing animation
- Arrow-release animation
- Target-hit reaction
- Jump and landing
- Teacher's pointing gesture

### Audio

- Bowstring tension
- Arrow release
- Target impact
- Footsteps on dirt
- Wooden training-dummy impacts

### Prototype objective

Hit 8 out of 10 training targets and complete a basic movement challenge.

**Success condition:** Unlock the precision-archery ability.

---

## Level 3: Rama Meets Sage Vishwamitra

### Game concept

**Genre:** Forest exploration and introductory combat.

### Contextual actions

- Follow Vishwamitra through the forest.
- Protect a ritual area.
- Identify enemies entering the clearing.
- Shoot approaching enemies.
- Defend designated ritual objects.

### Characters

- Rama
- Lakshmana
- Vishwamitra
- Enemies disrupting the ritual

### Powers

- Basic archery
- Charged arrow
- Defensive focus

### Background

A forest with:

- Tall trees
- Hanging vines
- Mossy rocks
- A small river
- A ceremonial fire
- Ancient stone structures

### Rooms

- Forest entrance
- Narrow woodland path
- Ritual clearing
- Rocky enemy approach

### Tilemap

Create forest ground, roots, rocks, platforms, and collision boundaries.

Use separate decorative layers for tree trunks, leaves, and distant mountains.

### Physics

- Projectile collision
- Enemy movement
- Hit detection
- Knockback
- Platform collision

### Mathematics

- Distance-based enemy detection
- Angles for aiming
- Health calculations
- Vector direction
- Cooldown timers

### Animation

- Forest idle pose
- Bow aiming
- Arrow release
- Enemy attack
- Enemy defeat
- Fire flicker
- Leaves moving in the wind

### Audio

- Forest ambience
- Bird calls
- Bow sounds
- Magical impact effects
- Ritual bells
- Enemy warning sounds

### Prototype objective

Protect the ritual for three waves of enemies.

**Success condition:** Complete the ritual defense and unlock the next chapter.

---

## Level 4: Rama Wins Sita's Hand in Marriage 💍

### Game concept

**Genre:** Precision challenge and cinematic story level.

### Contextual actions

- Enter King Janaka's court.
- Explore the palace hall.
- Interact with the bow of Shiva.
- Complete a strength-and-control interaction.
- Trigger the bow-breaking cinematic.
- Experience the marriage sequence.

### Characters

- Rama
- Sita
- King Janaka
- Lakshmana
- Court attendants
- Other participants

### Powers

No new combat power is necessary.

Introduce a special interaction system for legendary objects.

### Environment

A large palace hall with decorative pillars, royal banners, lamps, and the ceremonial bow.

### Rooms

- Palace entrance
- Main court
- Bow challenge platform
- Celebration hall

### Grid-based layout

Use a symmetrical composition, with the bow placed at the center of the main hall.

Keep the player, bow, and audience visually separated.

### Physics

- Object interaction
- Animation-driven movement
- Cinematic camera movement
- Triggered events

### Mathematics

- Rotation interpolation
- Scaling
- Timing curves
- Object alignment
- Progress interpolation

### Animation

- Rama's walking animation
- Bow inspection
- Strength pose
- Bow bending
- Cinematic bow-breaking effect
- Sita and Rama's marriage sequence

### Audio

- Palace ambience
- Orchestral swell
- Ceremonial bells
- Bow creaking
- Dramatic breaking sound
- Wedding music

### Prototype objective

Complete the ceremonial interaction and unlock the marriage cinematic.

**Success condition:** Finish the ceremony sequence.

---

## Level 5: Kaikeyi Demands Two Boons

### Game concept

**Genre:** Narrative adventure and dialogue exploration.

### Contextual actions

- Explore the royal palace.
- Visit the royal chambers.
- Interact with Kaikeyi, Manthara, and Dasharatha.
- Discover the events leading to the exile.
- Make dialogue selections that reveal different perspectives without changing the canonical outcome.

### Characters

- Kaikeyi
- Manthara
- Dasharatha
- Rama
- Palace attendants

### Powers

No combat abilities are needed.

Introduce:

- Dialogue interaction
- Story flags
- Quest progression
- Cinematic triggers

### Environment

A palace that initially appears festive but becomes visually subdued as the story progresses.

### Rooms

- Royal corridor
- Kaikeyi's chamber
- Throne room
- Palace balcony

### Tilemap

Use palace walls, doors, pillars, carpets, and decorative objects.

### Physics

- Basic movement
- Collision detection
- Interaction triggers
- Camera framing

### Mathematics

- Dialogue-state logic
- Boolean story flags
- Conditional transitions
- Event sequencing

Example:

```
if boon_one_revealed and boon_two_revealed:
    start_exile_cinematic()
```

### Animation

- Kaikeyi's idle pose
- Manthara's whispering gesture
- Dasharatha's distressed reaction
- Rama's calm listening pose
- Guards shifting position

### Audio

- Low ambient strings
- Footsteps on marble
- Door-opening sounds
- Quiet dialogue ambience
- Dramatic musical transition

### Prototype objective

Discover both boons and witness the decision that sends Rama into exile.

**Success condition:** Trigger the exile sequence.

---

## Level 6: Rama Goes into Exile 🌳

### Game concept

**Genre:** Side-scrolling exploration and survival-lite adventure.

### Contextual actions

- Leave Ayodhya.
- Travel through forest paths.
- Collect basic supplies.
- Cross streams and small gaps.
- Avoid environmental hazards.
- Discover resting places.

### Characters

- Rama
- Sita
- Lakshmana
- Citizens encountered during the departure

### Powers

- Archery
- Jumping
- Defensive movement
- Companion interaction

### Environment

The environment transitions from palace architecture to rural roads, rivers, and forests.

### Rooms

- Ayodhya gate
- Village road
- River crossing
- Forest camp
- Rocky woodland

### Tilemap

Create:

- Grass tiles
- Dirt paths
- Water tiles
- Tree trunks
- Rock platforms
- Climbable vines
- Camp objects

### Physics

- Gravity
- Jumping
- Moving platforms
- Water collision zones
- Ground friction
- Camera following

### Mathematics

- Jump height
- Movement speed
- Collision bounds
- Camera dead zones
- Path length

For an idealized vertical jump:

$$
H=\frac{v_0^2}{2g}
$$

where $H$ is maximum jump height, $v_0$ is initial vertical velocity, and $g$ is gravity magnitude.

### Animation

- Walking and running
- Carrying a bow
- Jumping
- Landing
- Sitting by a campfire
- Sita's walking animation
- Lakshmana's alert stance

### Audio

- Forest ambience
- River sounds
- Footsteps on grass
- Wind
- Campfire crackling
- Soft emotional music

### Prototype objective

Travel through the forest and reach the first exile campsite.

**Success condition:** Reach the designated camp and complete the story checkpoint.

---

## Level 7: King Dasharatha Dies

### Game concept

**Genre:** Cinematic narrative chapter.

### Contextual actions

- Explore a quiet palace.
- Speak with royal attendants.
- Witness Bharata's return.
- Discover Dasharatha's emotional condition.
- Trigger the death and mourning sequence.

### Characters

- Dasharatha
- Bharata
- Kaushalya
- Kaikeyi
- Shatrughna
- Royal attendants

### Powers

No combat or special powers.

### Environment

Use dimmer lighting, subdued colors, and reduced environmental movement.

### Rooms

- Royal bedroom
- Palace corridor
- Quiet courtyard
- Royal assembly hall

### Physics

- Character movement
- Camera framing
- Cinematic transitions
- Animation timing

### Mathematics

- Timeline sequencing
- Smooth camera interpolation
- State transitions
- Event timing

### Animation

- Slow walking
- Characters lowering their heads
- Bharata's shocked reaction
- Dasharatha resting
- Lamps flickering subtly
- Curtains moving gently

### Audio

- Low strings
- Soft wind
- Quiet footsteps
- Restrained ceremonial ambience
- Brief silence during key story moments

### Prototype objective

Complete the palace narrative and reveal Bharata's decision.

**Success condition:** Unlock Level 8.

The scene should convey grief without graphic imagery.

---

## Level 8: Bharata Refuses the Throne

### Game concept

**Genre:** Exploration, dialogue, and a short pilgrimage sequence.

### Contextual actions

- Explore the royal court.
- Witness Bharata's refusal to accept the throne.
- Travel toward Rama's forest dwelling.
- Interact with Rama and Lakshmana.
- Present Rama's sandals as the symbol of rightful rule.

### Characters

- Bharata
- Rama
- Lakshmana
- Sita
- Shatrughna
- Royal attendants

### Powers

- Dialogue choices
- Story-object interaction
- Travel navigation

### Environment

Royal chambers contrast with a simple forest dwelling.

### Rooms

- Throne room
- Palace courtyard
- Forest road
- Hermitage
- Return path

### Tilemap

Use palace tiles for the opening section and forest tiles for the second half.

### Physics

- Walking
- Basic jumping
- Object interaction
- Camera transitions

### Mathematics

- Navigation coordinates
- Path distance
- Dialogue-state management
- Event sequencing

### Animation

- Bharata's respectful bow
- Rama's calm response
- Sandals being placed on the throne
- Procession movement
- Flags moving in the wind

### Audio

- Soft flute
- Footsteps
- Palace ambience
- Forest ambience
- Gentle ceremonial music

### Prototype objective

Complete Bharata's journey and place the sandals on the throne.

**Success condition:** Unlock the forest encounter chapter.

---

## Level 9: Surpanakha's Encounter with Rama and Lakshmana

### Game concept

**Genre:** Dialogue encounter and short combat sequence.

### Contextual actions

- Explore the forest.
- Encounter Surpanakha.
- Trigger a dialogue sequence.
- Respond to her approach.
- Experience the confrontation with Lakshmana.
- Continue the story after she leaves.

### Characters

- Rama
- Lakshmana
- Surpanakha
- Optional forest creatures

### Powers

- Basic movement
- Defensive stance
- Short combat interactions

### Environment

A dense forest clearing surrounded by rocks, roots, and large trees.

### Rooms

- Forest trail
- Clearing
- Rocky escape path

### Tilemap

Use dense foliage and layered tree trunks. Keep the confrontation area unobstructed so players can read character movement.

### Physics

- Character collision
- Triggered dialogue
- Basic attack hitboxes
- Knockback for ordinary enemies

### Mathematics

- Character distance
- Facing direction
- Attack timing
- Dialogue state logic

### Animation

- Surpanakha approaching
- Dialogue gestures
- Rama's neutral stance
- Lakshmana's defensive movement
- Surpanakha retreating

### Audio

- Forest ambience
- Dialogue cues
- Short dramatic sting
- Running footsteps
- Wind through trees

### Prototype objective

Complete the encounter and reach the next forest area.

**Success condition:** Trigger the transition leading to the Golden Deer chapter.

Treat the confrontation as a non-graphic story sequence.

---

## Level 10: The Golden Deer

### Game concept

**Genre:** Tracking puzzle and chase platformer.

### Contextual actions

- Observe the golden deer.
- Follow it through a forest.
- Aim at distant targets or environmental markers.
- Navigate moving platforms.
- Investigate unusual movement patterns.
- Trigger Maricha's deceptive call.

### Characters

- Rama
- Sita
- Lakshmana
- Maricha in golden-deer form

### Powers

- Precision aiming
- Sprinting
- Jumping
- Environmental interaction

### Environment

A luminous forest with golden plants, mossy rocks, streams, and magical particles.

### Rooms

- Forest cottage
- Golden clearing
- Deer trail
- Rocky pursuit path
- Distant forest boundary

### Tilemap

Use:

- Forest ground
- Platforms
- Small cliffs
- Decorative grass
- Tree canopies
- Chase markers

### Physics

- Acceleration
- Jumping
- Moving targets
- Trigger volumes
- Collision detection

### Mathematics

- Relative velocity
- Target tracking
- Distance between objects
- Parabolic trajectories
- Timed chase conditions

Relative position is:

$$
\vec r=\vec p_{\text{deer}}-\vec p_{\text{Rama}}
$$

The direction of this vector helps determine where the player should aim or move.

### Animation

- Deer idle
- Deer grazing
- Deer sprinting
- Rama aiming
- Rama running
- Leaves scattering
- Magical shimmer

### Audio

- Forest ambience
- Delicate bell-like deer sounds
- Running footsteps
- Arrow release
- Magical sound cues
- Maricha's distant call

### Prototype objective

Follow the golden deer through three chase sections and reach the designated story trigger.

**Success condition:** Activate the event that draws Rama away from the cottage.

---

## Level 11: Ravana Abducts Sita 👹

### Game concept

**Genre:** Story-driven escape sequence and aerial encounter.

### Contextual actions

- Return to the cottage area through a short cinematic transition.
- Experience Ravana's arrival in disguise.
- Trigger Sita's abduction.
- Control Jatayu during a brief aerial sequence.
- Attempt to intercept Ravana's flying chariot.
- Witness Jatayu's defeat.

### Characters

- Sita
- Ravana
- Jatayu
- Rama and Lakshmana in transition scenes

### Powers

- Jatayu's flight
- Aerial movement
- Limited aerial attack
- Short evasive movement

### Environment

A forest clearing transitions into a sky above forests, cliffs, and distant mountains.

### Rooms or stages

- Hermitage clearing
- Forest edge
- Aerial chase
- Rocky landing site

### Tilemap

Use forest tiles for the opening and separate aerial background layers for the chase.

The sky section can use invisible collision boundaries rather than a traditional ground tilemap.

### Physics

- Flying movement
- Acceleration and drag
- Aerial collision
- Moving-target tracking
- Knockback

### Mathematics

- Two-dimensional vectors
- Relative position
- Flight velocity
- Distance-based pursuit
- Camera tracking

### Animation

- Ravana's disguise transition
- Chariot movement
- Sita's reaction
- Jatayu's wing flaps
- Aerial dive
- Jatayu landing

### Audio

- Wind
- Wing flaps
- Chariot movement
- Dramatic orchestral music
- Aerial impacts
- Music fading during the aftermath

### Prototype objective

Control Jatayu during the aerial pursuit and attempt to reach Ravana.

**Success condition:** Complete the story encounter and transition to Rama's search.

This sequence should communicate Jatayu's courage without graphic violence.

---

## Level 12: Rama Meets Hanuman 🙏

### Game concept

**Genre:** Exploration, character introduction, and companion tutorial.

### Contextual actions

- Search the rocky landscape.
- Discover Hanuman.
- Complete a dialogue sequence.
- Follow Hanuman to Sugriva.
- Learn the companion-following system.
- Solve a small traversal puzzle together.

### Characters

- Rama
- Lakshmana
- Hanuman
- Sugriva, introduced at the end

### Powers

- Companion commands
- Basic archery
- Hanuman's short leap
- Cooperative interactions

### Environment

Rocky hills, caves, trees, and mountain paths.

### Rooms

- Rocky trail
- Mountain overlook
- Cave entrance
- Meeting area

### Tilemap

Use cliff tiles, rocky platforms, vines, and background mountains.

### Physics

- Platform collision
- Jumping
- Character following
- Ground detection
- Moving platforms

### Mathematics

- Follow distance
- Vector interpolation
- Pathfinding
- Platform jump calculations

A simple companion-following rule can be:

$$
\vec v_{\text{Hanuman}}=k(\vec p_{\text{target}}-\vec p_{\text{Hanuman}})
$$

where $k$ controls the follow response.

### Animation

- Hanuman's expressive idle
- Tail movement
- Greeting gesture
- Jumping
- Rama and Lakshmana listening
- Companion follow animation

### Audio

- Mountain wind
- Footsteps on stone
- Hanuman's landing sound
- Friendly musical theme
- Dialogue ambience

### Prototype objective

Meet Hanuman and complete a cooperative traversal challenge.

**Success condition:** Unlock companion support.

---

## Level 13: Rama Forms an Alliance with Sugriva

### Game concept

**Genre:** Story-driven action and a combat challenge.

### Contextual actions

- Explore Sugriva's refuge.
- Learn about his conflict with Vali.
- Witness the confrontation involving the two brothers.
- Complete a short combat or archery challenge.
- Help Sugriva regain his position.
- Activate the alliance sequence.

### Characters

- Rama
- Lakshmana
- Hanuman
- Sugriva
- Vali

### Powers

- Archery
- Companion assistance
- Defensive focus

### Environment

A rocky mountain region with a forest arena and ancient structures.

### Rooms

- Sugriva's refuge
- Mountain path
- Arena
- Alliance meeting area

### Tilemap

Create cliffs, arena platforms, rocks, and a small ceremonial meeting area.

### Physics

- Melee hitboxes
- Projectile collision
- Knockback
- Ground friction
- Character movement

### Mathematics

- Health and damage values
- Collision geometry
- Attack cooldowns
- Distance-based targeting
- State machines

### Animation

- Sugriva's idle
- Vali's combat stance
- Running and jumping
- Rama's aiming animation
- Alliance gesture
- Victory reaction

### Audio

- Rocky-landscape ambience
- Heavy footsteps
- Combat impacts
- Bow sounds
- Dramatic victory music

### Prototype objective

Complete the confrontation sequence and establish the alliance with Sugriva.

**Success condition:** Unlock the search-for-Sita mission.

Because different Ramayana tellings narrate the Vali episode differently, the game should identify the version it follows.

---

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

## Level 15: Hanuman Meets Sita

### Game concept

**Genre:** Stealth exploration and story interaction.

### Contextual actions

- Explore Lanka's palace gardens.
- Avoid patrol routes.
- Find the Ashoka grove.
- Identify Sita.
- Approach her without alarming nearby guards.
- Present Rama's ring.
- Trigger the conversation.

### Characters

- Hanuman
- Sita
- Ravana's guards
- Ravana, in a short story sequence

### Powers

- Stealth movement
- Short leaps
- Environmental hiding
- Contextual interaction

### Environment

A beautiful garden with flowering trees, stone paths, ornamental pools, and the Ashoka tree.

### Rooms

- Lanka rooftop
- Palace garden
- Guard patrol route
- Ashoka grove

### Tilemap

Use garden floor tiles, hedge obstacles, walls, platforms, and decorative tree layers.

### Physics

- Ground movement
- Collision detection
- Line-of-sight checks
- Jumping
- Trigger volumes

### Mathematics

- Patrol paths
- Visibility cones
- Distance checks
- Timing and synchronization

For a simple stealth system, detection may depend on whether Hanuman is within a guard's viewing range and inside its viewing angle.

### Animation

- Hanuman's cautious walk
- Crouching
- Guard patrol
- Sita's idle animation
- Ring presentation
- Emotional reaction

### Audio

- Garden ambience
- Leaves rustling
- Guard footsteps
- Soft bells
- Quiet flute
- Subtle musical theme

### Prototype objective

Reach Sita and present Rama's ring.

**Success condition:** Complete the conversation and unlock the escape sequence.

---

## Level 16: Hanuman Sets Lanka Ablaze 🔥

### Game concept

**Genre:** Escape platformer and environmental action.

### Contextual actions

- Trigger Hanuman's capture.
- Witness the tail-burning episode.
- Escape the guarded area.
- Navigate rooftops.
- Jump between buildings.
- Activate controlled environmental fire effects.
- Reach the city outskirts.

### Characters

- Hanuman
- Ravana
- Lanka guards

### Powers

- Powerful leap
- Rooftop traversal
- Environmental interaction
- Escape movement

### Environment

A stylized city of golden towers, stone walls, rooftops, and illuminated streets.

### Rooms or stages

- Guarded courtyard
- Palace rooftop
- Market street
- Tower section
- City outskirts

### Tilemap

Create:

- Rooftop tiles
- Building facades
- Balcony platforms
- Decorative arches
- Fire-hazard zones
- Safe landing surfaces

### Physics

- Jumping
- Gravity
- Platform collision
- Moving hazards
- Triggered environmental events

### Mathematics

- Jump trajectory
- Collision rectangles
- Timing windows
- Camera tracking
- Distance between platforms

### Animation

- Hanuman's tail movement
- Running and jumping
- Fire flicker
- Guards reacting
- Rooftop landing
- Smoke drifting upward

### Audio

- Fire crackling
- Alarm bells
- Running footsteps
- Rooftop impacts
- Wind
- Fast-paced percussion

### Prototype objective

Escape the city by traversing a series of rooftops.

**Success condition:** Reach the outskirts and report Sita's location to Rama.

The fire should be stylized rather than graphically destructive, and the level should avoid depicting civilians as targets.

---

## Level 17: The Bridge to Lanka Is Built

### Game concept

**Genre:** Construction puzzle and cooperative exploration.

### Contextual actions

- Explore the coastline.
- Collect suitable building materials.
- Move stones to marked positions.
- Coordinate with vanara workers.
- Activate bridge sections.
- Cross the completed bridge.

### Characters

- Rama
- Lakshmana
- Hanuman
- Sugriva
- Vanara workers

### Powers

- Strength-based interaction
- Companion commands
- Object manipulation

### Environment

A wide coastline with ocean waves, rocky cliffs, and a long bridge extending toward Lanka.

### Rooms

- Coastal camp
- Material collection zone
- Construction area
- Completed bridge
- Lanka approach

### Tilemap

Use a grid to align bridge pieces.

A conceptual grid may represent each placement location with a cell coordinate:

$$
(i,j)
$$

where $i$ is the horizontal cell index and $j$ is the vertical cell index.

### Physics

- Object movement
- Basic rigidbody simulation
- Collision detection
- Buoyancy-like visual effects, if desired
- Triggered construction events

### Mathematics

- Grid snapping
- Object placement
- Resource counting
- Coordinate transformations
- Puzzle-state logic

### Animation

- Workers carrying stones
- Stones being placed
- Bridge sections appearing
- Hanuman lifting objects
- Waves moving
- Flags fluttering

### Audio

- Ocean waves
- Stone impacts
- Workers' activity
- Rope sounds
- Construction percussion
- Rising orchestral music

### Prototype objective

Complete three bridge-building puzzles.

**Success condition:** Construct a traversable bridge and reach Lanka.

For a prototype, the bridge can be assembled from predefined pieces rather than requiring fully simulated construction.

---

## Level 18: The Great War Between Rama and Ravana ⚔️

### Game concept

**Genre:** 2D action combat and battlefield survival.

### Contextual actions

- Enter the battlefield.
- Defeat groups of ordinary enemies.
- Protect allied characters.
- Fight a mini-boss.
- Switch between Rama and Hanuman in selected encounters.
- Rescue Lakshmana after his injury.
- Control Hanuman during the Sanjeevani mountain sequence.

### Characters

- Rama
- Lakshmana
- Hanuman
- Sugriva
- Indrajit
- Kumbhakarna
- Vanara warriors
- Lanka's warriors

### Powers

- Archery
- Charged arrow
- Defensive focus
- Hanuman's leap
- Team attacks
- Special rescue ability

### Environment

A large battlefield with fortifications, rocky ground, banners, distant towers, and dramatic skies.

### Rooms or stages

1. Battlefield entrance
2. First combat zone
3. Indrajit's encounter
4. Lakshmana's injury sequence
5. Sanjeevani mountain
6. Return to the battlefield

### Tilemap

Use modular ground tiles, stone barricades, rocks, broken structures, and decorative battlefield objects.

Avoid filling every tile with decoration. Keep combat lanes readable.

### Physics

- Projectile motion
- Hitboxes and hurtboxes
- Knockback
- Ground collision
- Jumping
- Enemy collision
- Moving hazards

### Mathematics

- Damage calculations
- Health bars
- Projectile angles
- Enemy state machines
- Cooldown timers
- Wave progression

Example damage calculation:

$$
D_{\text{final}}=\max(1,D_{\text{base}}-A_{\text{defense}})
$$

Here, $D_{\text{base}}$ is the incoming damage and $A_{\text{defense}}$ is a simplified defense value.

### Animation

- Running
- Bow aiming
- Arrow release
- Enemy attacks
- Heavy enemy ground slam
- Hit reactions
- Hanuman's mountain-carrying animation
- Healing sequence

### Audio

- Battlefield ambience
- Bow releases
- Arrows hitting shields
- Heavy footsteps
- Magical attack effects
- Battle drums
- Healing music

### Prototype objective

Complete the battlefield encounters and rescue Lakshmana through the Sanjeevani sequence.

**Success condition:** Finish the rescue and unlock the final battle.

This level should emphasize courage, teamwork, and sacrifice rather than graphic depictions of violence.

---

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

## Level 20: Rama Returns to Ayodhya 🪔

### Game concept

**Genre:** Narrative exploration, celebration, and ending sequence.

### Contextual actions

- Return to Ayodhya.
- Explore the decorated streets.
- Interact with celebrating citizens.
- Enter the royal palace.
- Witness Rama's coronation.
- Explore the kingdom after the ceremony.
- Unlock the post-game story gallery.

### Characters

- Rama
- Sita
- Lakshmana
- Bharata
- Hanuman
- Shatrughna
- Citizens and attendants

### Powers

No combat powers are necessary.

The final chapter emphasizes story completion and exploration.

### Environment

Ayodhya is transformed into a vibrant celebration with lamps, flowers, banners, and illuminated palace architecture.

### Rooms

- City gate
- Celebration street
- Public square
- Palace entrance
- Coronation hall
- Royal balcony

### Tilemap

Use palace tiles, decorative street tiles, steps, arches, lamps, and celebration props.

Use separate foreground layers for flowers, lamps, and banners.

### Physics

- Basic movement
- Crowd avoidance
- Interaction triggers
- Camera transitions
- Particle movement

### Mathematics

- Grid-based placement of decorative objects
- Camera interpolation
- Crowd positioning
- Particle emission rates
- Timeline synchronization

### Animation

- Rama's walking animation
- Sita's idle animation
- Bharata's welcoming gesture
- Hanuman's respectful pose
- Citizens celebrating
- Lamps flickering
- Flowers falling
- Flags waving
- Coronation sequence

### Audio

- Ceremonial music
- Flute and veena
- Bells
- Crowd ambience
- Footsteps
- Fire and lamp ambience
- Triumphant ending theme

### Prototype objective

Complete the return journey and witness Rama's coronation.

**Success condition:** Unlock the ending, story gallery, and optional free exploration.

The ending can celebrate the triumph of dharma and the restoration of rightful rule. It should not imply that all Ramayana traditions narrate every subsequent event identically.

---

# 7\. 2D Skeletal Animation System

Skeletal animation allows a character to move naturally without drawing a completely new image for every frame.

Instead, the character is divided into connected body parts, each attached to a bone.

## Suggested Rama skeleton

```
                 Head
                  |
                Neck
                  |
          Upper Torso
           /       \
      Left Arm    Right Arm
         |            |
     Forearm       Forearm
         |            |
        Hand         Hand
                  |
                Pelvis
                /    \
          Left Leg  Right Leg
              |        |
          Lower Leg Lower Leg
              |        |
             Foot     Foot
```

For archery, add a separate bow and string rig.

The bow arm should maintain a stable aiming pose while the other arm draws the string.

## Suggested Hanuman skeleton

Hanuman requires additional bones for expressive movement.

```
                 Head
                  |
                Neck
                  |
                Torso
               /     \
           Left Arm  Right Arm
                  |
                Pelvis
               /      \
          Left Leg   Right Leg

                Tail Root
                    |
                 Tail 1
                    |
                 Tail 2
                    |
                 Tail 3
                    |
                 Tail Tip
```

Use the tail to support balance, expressive gestures, and aerial movement.

## Sita's skeleton

Use a standard humanoid skeleton with additional bones or deformers for:

- Hair
- Long fabric elements
- Jewelry movement
- Garment sway

Avoid excessive secondary motion that interferes with readability.

## Required animation clips

| Animation | Typical duration | Purpose |
| --- | --- | --- |
| Idle | 1.5–3 seconds | Standing and breathing |
| Walk | 0.5–0.8 seconds | Normal movement |
| Run | 0.35–0.6 seconds | Faster movement |
| Jump start | 0.1–0.2 seconds | Takeoff |
| Jump loop | 0.2–0.5 seconds | Airborne movement |
| Landing | 0.15–0.3 seconds | Ground contact |
| Bow aim | 0.3–0.6 seconds | Target acquisition |
| Bow release | 0.15–0.3 seconds | Arrow launch |
| Hit reaction | 0.2–0.5 seconds | Taking damage |
| Dodge | 0.25–0.45 seconds | Evasion |
| Interact | 0.4–1.0 seconds | Contextual action |
| Victory | 1–2 seconds | Combat or story completion |
| Cinematic gesture | Variable | Dialogue and narrative |

These durations are starting points for tuning.

### Animation blending

Use animation states such as:

```
Idle
 ├── Walk
 ├── Run
 ├── Jump
 │    ├── Fall
 │    └── Land
 ├── Aim
 │    └── Shoot
 ├── Dodge
 ├── Hit
 └── Interact
```

Transitions should depend on movement speed, grounded state, player input, and combat state.

### Example state conditions

```
if grounded and speed < idle_threshold:
    animation = "Idle"

if grounded and speed >= walk_threshold:
    animation = "Walk"

if not grounded and vertical_velocity > 0:
    animation = "Jump"

if not grounded and vertical_velocity <= 0:
    animation = "Fall"
```

In production, use animation parameters and transition rules rather than repeatedly forcing animation states from unrelated scripts.

---

# 8\. Character Idle Animations

Idle animations are important because characters spend considerable time standing during dialogue, exploration, and story sequences.

Each major character should have an individual idle personality.

| Character | Idle animation |
| --- | --- |
| Rama | Gentle breathing, slight bow movement, cloth movement |
| Sita | Calm breathing, subtle head movement, fabric sway |
| Lakshmana | Alert stance, small shoulder movement, hand near bow |
| Hanuman | Breathing, tail swaying, occasional expressive head movement |
| Bharata | Upright posture, subtle head movement |
| Dasharatha | Slow breathing and gentle movement of royal garments |
| Vishwamitra | Calm stance, robe movement, occasional hand gesture |
| Sugriva | Alert stance, subtle head and shoulder movement |
| Ravana | Commanding posture, armor movement, slow head turn |
| Surpanakha | Expressive posture and controlled gestures |
| Jatayu | Feather movement, head turns, wing adjustments |
| Indrajit | Confident stance and subtle weapon movement |
| Kumbhakarna | Heavy breathing and slow body movement |

### Idle animation implementation

Use three layers of motion:

1. **Primary motion:** Body breathing and posture changes.
2. **Secondary motion:** Hair, clothing, jewelry, and tail movement.
3. **Environmental interaction:** Wind, lighting, and particles.

Idle animations should not be perfectly synchronized across all characters. Slight timing differences make groups appear more natural.

---

# 9\. Vector Art and Texture Design

## Vector art production

Create reusable vector assets for:

- Character bodies
- Faces
- Weapons
- Bows and arrows
- Crowns and ornaments
- Trees and foliage
- Buildings
- Rocks
- Lamps
- Decorative borders
- UI icons
- Dialogue portraits

### Suggested art pipeline

1. Create concept sketches.
2. Define the visual style.
3. Design character silhouettes.
4. Separate characters into riggable parts.
5. Create background layers.
6. Export vector art or rasterized sprites.
7. Rig characters.
8. Test animations in the game engine.
9. Optimize textures and atlases.

### Texture types

| Texture type | Purpose |
| --- | --- |
| Base color | Defines the main surface color |
| Alpha transparency | Removes the background around sprites |
| Normal map, optional | Adds lighting depth to 2D surfaces |
| Emission map, optional | Makes lamps and magical effects glow |
| Particle texture | Used for fire, dust, smoke, and magical effects |
| UI texture | Used for buttons, panels, and icons |

### Visual style recommendation

Use clean outlines and controlled color palettes for characters.

Use more painterly textures for distant environments.

This combination helps characters remain readable against detailed backgrounds.

### Asset optimization

- Reuse repeated props.
- Pack related sprites into atlases.
- Avoid unnecessarily large transparent textures.
- Compress mobile textures appropriately.
- Use skeletal animation for complex characters.
- Use sprite-sheet animation for simple effects such as fire and water.

---

# 10\. Background Design and Parallax

Each level should contain several background layers.

A typical arrangement is:

```
Layer 5: Foreground objects
Layer 4: Playable characters and gameplay objects
Layer 3: Near background
Layer 2: Middle background
Layer 1: Distant background
Layer 0: Sky or atmospheric color
```

The exact rendering order depends on the scene.

## Example: Forest background

- Sky gradient
- Distant mountain silhouettes
- Distant trees
- Midground trees
- Gameplay platforms
- Foreground leaves and branches

Move distant layers more slowly than foreground layers to create a sense of depth.

A simple parallax model is:

$$
x_{\text{layer}}=x_{\text{camera}}p
$$

where $p$ is the layer's parallax factor.

For example:

- Distant mountains: $p=0.1$
- Distant trees: $p=0.3$
- Near foliage: $p=0.7$
- Gameplay layer: $p=1.0$

These values are illustrative and should be adjusted to the camera setup.

## Background elements by environment

| Environment | Background elements |
| --- | --- |
| Ayodhya | Palace towers, banners, rooftops, city walls |
| Training grounds | Trees, targets, palace walls |
| Forest | Trees, vines, rocks, distant hills |
| Hermitage | Small huts, fire pits, foliage |
| Janaka's court | Pillars, curtains, decorative walls |
| Mountain region | Cliffs, caves, distant peaks |
| Ocean | Waves, islands, clouds, horizon |
| Lanka | Golden towers, walls, bridges, gardens |
| Battlefield | Fortifications, banners, smoke, distant structures |
| Final celebration | Lamps, flowers, flags, illuminated buildings |

Use foreground elements sparingly during combat. Decorative foliage should not hide enemies, projectiles, or hazards.

---

# 11\. Tilemaps and Grid-Based Level Design

Tilemaps make it easier to construct, edit, and optimize environments.

Instead of creating every level as one large image, divide the environment into reusable tiles.

## Recommended tile categories

### Terrain tiles

- Grass
- Dirt
- Stone
- Sand
- Water
- Cliff
- Marble
- Rooftop

### Structural tiles

- Walls
- Doors
- Platforms
- Pillars
- Stairs
- Arches
- Bridges

### Decorative tiles

- Flowers
- Grass tufts
- Moss
- Small stones
- Wall patterns
- Ground markings

### Interactive tiles and objects

- Switches
- Doors
- Pressure plates
- Collectibles
- Checkpoints
- Hazard zones
- Puzzle markers

## Grid-based layout

Use a conceptual grid to plan level geometry.

For example:

```
Level: Forest Path

+---+---+---+---+---+---+---+---+
| T | T |   |   |   | T | T | T |
+---+---+---+---+---+---+---+---+
|   |   |   | P |   |   |   |   |
+---+---+---+---+---+---+---+---+
|   | R |   | P |   | R |   |   |
+---+---+---+---+---+---+---+---+
| G | G | G | G | G | G | G | G |
+---+---+---+---+---+---+---+---+
```

Legend:

- `T` = Tree or foliage
- `P` = Platform
- `R` = Rock
- `G` = Ground

This diagram illustrates layout planning, not a complete playable map.

### Tilemap layers

Separate the tilemap into:

1. Background tiles
2. Decorative tiles
3. Solid collision tiles
4. Interactive tiles
5. Foreground tiles

Collision tiles should be independent of decorative tiles.

For example, a tree canopy may be decorative while its trunk has a solid collision shape.

### Grid coordinate conversion

For a grid with tile width $w$ and height $h$, a cell coordinate $(i,j)$ can be mapped to a world position:

$$
x=x_0+iw
$$

$$
y=y_0+jh
$$

Here, $(x_0,y_0)$ represents the grid origin.

Use the engine's built-in grid conversion functions where possible to avoid coordinate inconsistencies.

---

# 12\. Physics Concepts Used Across the Game

The game can teach physics concepts naturally through its mechanics.

| Physics concept | Application |
| --- | --- |
| Position | Character and object locations |
| Velocity | Movement speed and direction |
| Acceleration | Starting, stopping, and sprinting |
| Gravity | Jumping and falling |
| Projectile motion | Arrows and thrown objects |
| Collision detection | Contact with enemies and objects |
| Friction | Ground movement and stopping |
| Impulse | Knockback and impacts |
| Angular motion | Aiming and rotating weapons |
| Oscillation | Pendulums and decorative objects |
| Raycasting | Ground checks and line-of-sight detection |
| Trigger volumes | Collectibles and story events |
| Parallax | Layered background movement |
| Spring-like motion | Secondary animation of tails and clothing |
| Particle systems | Fire, smoke, dust, and magical effects |

### Example: Arrow physics

An arrow may use a fixed launch velocity:

$$
v_x=v\cos\theta
$$

$$
v_y=v\sin\theta
$$

where:

- $v$ is the initial arrow speed.
- $\theta$ is the firing angle.
- $v_x$ is horizontal velocity.
- $v_y$ is vertical velocity.

If air resistance is ignored, gravity changes the vertical component of velocity over time.

For a game, you can choose between:

- Simulated physical arrows
- Predetermined ballistic trajectories
- Homing or guided arrows for selected abilities

Physical arrows suit the archery training level, while scripted trajectories may be more suitable for cinematic attacks.

---

# 13\. Mathematics Concepts Used Across the Game

Mathematics supports movement, animation, combat, puzzles, and camera control.

| Mathematics concept | Game application |
| --- | --- |
| Cartesian coordinates | Character positions |
| Vectors | Movement and aiming |
| Trigonometry | Arrow angles and circular movement |
| Linear equations | Constant-speed movement |
| Quadratic equations | Jump trajectories |
| Interpolation | Smooth camera and animation movement |
| Geometry | Hitboxes and collision shapes |
| Distance formula | Enemy range and interaction distance |
| Dot product | Facing direction and vision cones |
| Probability | Optional random loot or enemy behavior |
| Boolean logic | Quest conditions and switches |
| Graph theory | Room connections and navigation |
| Matrices and transformations | Object rotation, scaling, and positioning |
| Timelines | Cinematics and animation events |
| State machines | Character and enemy behavior |
| Resource arithmetic | Health, energy, and collectibles |

### Example: Interaction distance

Suppose Rama can interact with an object within a distance of $d_{\max}$.

Calculate:

$$
d=\sqrt{(x_o-x_r)^2+(y_o-y_r)^2}
$$

where:

- $(x_o,y_o)$ is the object's position.
- $(x_r,y_r)$ is Rama's position.

Interaction is allowed if:

$$
d\leq d_{\max}
$$

For performance, you can compare squared distances instead of calculating the square root.

### Example: Enemy detection

An enemy may attack when:

- The player is within a detection radius.
- The player is in the enemy's facing direction.
- The enemy is not stunned.
- The attack cooldown has expired.

Combining these conditions creates predictable enemy behavior.

---

# 14\. Audio Design and Sound Effects

Audio should support both gameplay and storytelling.

Use three main audio categories.

## A. Music

Create original music inspired by suitable Indian musical traditions and cinematic orchestration.

Suggested themes:

- Ayodhya theme
- Rama's training theme
- Forest exploration theme
- Sita and Rama theme
- Hanuman's adventure theme
- Lanka infiltration theme
- Battlefield theme
- Ravana boss theme
- Return-to-Ayodhya theme

Avoid treating every story event as an action scene. Quiet narrative sections need space for dialogue and emotion.

## B. Sound effects

### Character sounds

- Footsteps on grass
- Footsteps on stone
- Jump takeoff
- Landing
- Bowstring tension
- Arrow release
- Weapon impact
- Cloth movement
- Tail movement
- Character interaction

### Environment sounds

- Wind
- Water
- Birds
- Leaves
- Fire
- Distant crowds
- Palace ambience
- Ocean waves
- Temple bells
- Construction sounds

### Gameplay sounds

- Collectible pickup
- Puzzle solved
- Door unlocked
- Quest completed
- Player damaged
- Enemy defeated
- Checkpoint activated
- Boss phase change
- Victory cue

## C. Audio implementation

Use an audio manager to control:

- Music playback
- Music transitions
- Environmental ambience
- Sound-effect volume
- Dialogue volume
- Spatial audio, where appropriate
- Audio settings

Avoid playing every sound at full volume simultaneously.

Use sound priorities and limited voice counts to prevent repeated footsteps or combat effects from overwhelming the mix.

### Suggested audio asset organization

```
Audio/
├── Music/
│   ├── Ayodhya.wav
│   ├── Forest.wav
│   ├── Lanka.wav
│   ├── Battlefield.wav
│   └── Ending.wav
├── Characters/
│   ├── Rama/
│   ├── Sita/
│   ├── Hanuman/
│   └── Ravana/
├── Environment/
│   ├── Forest/
│   ├── Ocean/
│   ├── Palace/
│   └── Battlefield/
└── UI/
    ├── Confirm.wav
    ├── Cancel.wav
    └── QuestComplete.wav
```

For production, use compressed audio formats appropriate to the engine and target platform.

---

# 15\. Textures, Visual Effects, and Lighting

Although the game is 2D, textures and lighting can create depth.

### Recommended effects

- Soft glow around lamps
- Fire and smoke particles
- Water ripples
- Dust during heavy landings
- Magical glows for selected story abilities
- Gentle highlights on golden objects
- Light shafts through forest canopies
- Atmospheric haze around distant mountains

### Texture guidelines

- Keep character outlines readable.
- Use normal maps only when the visual style benefits from simulated lighting.
- Avoid excessive texture noise.
- Use emission sparingly.
- Maintain consistent light direction within each environment.
- Make hazards visually distinct from decoration.

### Performance guidelines

For mobile:

- Reduce unnecessary particle counts.
- Limit overlapping real-time lights.
- Use sprite atlases.
- Reuse materials.
- Keep large background textures within memory limits.

---

# 16\. Prototype Architecture

A working prototype should separate gameplay systems from story content.

## Suggested project structure

```
RamayanaGame/
├── Assets/
│   ├── Art/
│   │   ├── Characters/
│   │   ├── Environments/
│   │   ├── Tiles/
│   │   ├── Props/
│   │   └── UI/
│   ├── Animation/
│   ├── Audio/
│   ├── Materials/
│   ├── Prefabs/
│   ├── Scenes/
│   │   ├── Level01_Birth/
│   │   ├── Level02_Training/
│   │   ├── Level03_Vishwamitra/
│   │   └── ...
│   ├── Scripts/
│   │   ├── Player/
│   │   ├── Combat/
│   │   ├── Enemies/
│   │   ├── Animation/
│   │   ├── Story/
│   │   ├── Dialogue/
│   │   ├── Camera/
│   │   ├── Audio/
│   │   └── UI/
│   └── Tilemaps/
└── Documentation/
```

## Core systems

### Player controller

Handles:

- Movement
- Jumping
- Ground detection
- Aiming
- Combat input
- Interaction input

### Character controller

Handles:

- Health
- Damage
- Animation state
- Faction
- Abilities

### Story manager

Handles:

- Current chapter
- Story flags
- Cinematic triggers
- Level progression
- Canonical story outcomes

### Dialogue manager

Handles:

- Dialogue text
- Character portraits
- Dialogue choices
- Dialogue progression
- Localization

### Level manager

Handles:

- Loading scenes
- Checkpoints
- Objectives
- Level completion
- Restarting

### Audio manager

Handles:

- Music
- Sound effects
- Volume controls
- Audio transitions

### Save system

Stores:

- Unlocked chapters
- Completed objectives
- Player settings
- Collectibles
- Optional lore entries

---

# 17\. Example Prototype Code: Basic 2D Player Movement

The following is a minimal Unity C# starting point for a 2D character using a `Rigidbody2D`.

It assumes the project uses Unity's conventional horizontal input axis and that jumping is triggered by a key press.

```
using UnityEngine;

[RequireComponent(typeof(Rigidbody2D))]
public class RamaController : MonoBehaviour
{
    [SerializeField] private float moveSpeed = 5f;
    [SerializeField] private float jumpForce = 9f;
    [SerializeField] private Transform groundCheck;
    [SerializeField] private LayerMask groundLayer;

    private Rigidbody2D rb;
    private float horizontalInput;
    private bool jumpRequested;

    private void Awake()
    {
        rb = GetComponent<Rigidbody2D>();
    }

    private void Update()
    {
        horizontalInput = Input.GetAxisRaw("Horizontal");

        if (Input.GetKeyDown(KeyCode.Space))
        {
            jumpRequested = true;
        }
    }

    private void FixedUpdate()
    {
        rb.linearVelocity = new Vector2(
            horizontalInput * moveSpeed,
            rb.linearVelocity.y
        );

        if (jumpRequested && IsGrounded())
        {
            rb.linearVelocity = new Vector2(
                rb.linearVelocity.x,
                jumpForce
            );
        }

        jumpRequested = false;
    }

    private bool IsGrounded()
    {
        if (groundCheck == null)
            return false;

        return Physics2D.OverlapCircle(
            groundCheck.position,
            0.15f,
            groundLayer
        ) != null;
    }
}
```

**Compatibility note:** This uses `Rigidbody2D.linearVelocity`, as supported in recent Unity versions. Older Unity versions may require `Rigidbody2D.velocity`. Configure the input system and physics settings for your chosen Unity version.

### Setup instructions

1. Create a 2D project.
2. Import the Rama character sprite or skeletal rig.
3. Add a `Rigidbody2D` and suitable collider.
4. Add an empty child object called `GroundCheck`.
5. Place it near Rama's feet.
6. Create a ground layer.
7. Assign the ground layer to the script.
8. Place solid ground tiles in the scene.
9. Attach the script to Rama.
10. Test walking and jumping.

This provides the initial movement foundation. Archery, enemy combat, animation, dialogue, and chapter progression should be added as separate systems.

---

# 18\. Example Prototype Code: Story Event Progression

All 20 chapters should share one story-progression system.

A simplified Unity implementation is:

```
using UnityEngine;
using UnityEngine.SceneManagement;

public class StoryProgression : MonoBehaviour
{
    [SerializeField] private string nextSceneName;

    private bool completed;

    public void CompleteCurrentEvent()
    {
        if (completed)
            return;

        completed = true;

        Debug.Log("Story event completed.");

        if (!string.IsNullOrEmpty(nextSceneName))
        {
            SceneManager.LoadScene(nextSceneName);
        }
    }
}
```

Attach this component to an event manager or a dedicated story-trigger object.

Call `CompleteCurrentEvent()` after the chapter's objective is fulfilled.

For a full game, add save data and transition handling so that story progress is preserved.

---

# 19\. Recommended Prototype Scope

Building all 20 levels at full quality is a substantial project. The best approach is to create one polished vertical slice first.

A vertical slice is a small but functional section of the final game that demonstrates the intended visual quality, gameplay, audio, and technical systems.

## Phase 1: Core prototype

Build these three levels first:

1. **Rama's Childhood and Education** — movement, archery, physics, and animation.
2. **Rama Goes into Exile** — exploration, tilemaps, and environmental puzzles.
3. **Hanuman Travels to Lanka** — aerial movement and special abilities.

Together, they demonstrate the core systems needed by the rest of the game.

## Phase 2: Narrative systems

Implement:

- Dialogue
- Cinematics
- Story flags
- Character interactions
- Chapter transitions
- Save and load
- Collectibles and lore

## Phase 3: Combat systems

Implement:

- Enemy AI
- Archery
- Hitboxes
- Health and damage
- Boss state machines
- Companion support
- Combat animations

## Phase 4: Visual and audio polish

Add:

- Skeletal animation
- Parallax backgrounds
- Particle effects
- Music
- Sound effects
- Lighting
- UI transitions

## Phase 5: Full 20-event campaign

Reuse the established systems to produce the remaining chapters.

Reuse should apply to technology and art assets, not to the narrative itself: each event should retain its own atmosphere, contextual actions, and story purpose.

---

# 20\. Final Game Design Summary

The complete game combines storytelling, exploration, action, puzzle-solving, physics, mathematics, and 2D animation.

| System | Role in the game |
| --- | --- |
| Contextual actions | Make each story event interactive |
| Character design | Give heroes and antagonists recognizable identities |
| Powers | Provide story-appropriate gameplay abilities |
| Vector art | Create scalable character and environment assets |
| Skeletal animation | Animate characters efficiently |
| Idle animation | Make characters feel alive |
| Tilemaps | Build reusable level geometry |
| Grid-based layouts | Organize rooms and puzzles |
| Physics | Control movement, jumping, arrows, and collisions |
| Mathematics | Support aiming, animation, navigation, and combat |
| Textures | Add surface detail |
| Backgrounds | Establish atmosphere and visual depth |
| Rooms | Organize exploration and story progression |
| Frames and animation | Communicate movement and character emotion |
| Audio | Support gameplay feedback and storytelling |
| Sound effects | Make actions readable and satisfying |
| Music | Establish mood and reinforce dramatic moments |
| Prototype architecture | Make the project maintainable |
| Story progression | Connect all 20 events into a coherent campaign |

## Recommended first playable prototype

Start with a small, polished demo containing:

- Rama's idle, walk, jump, and archery animations.
- A forest environment built with tilemaps.
- One enemy type.
- One interactive story object.
- A simple dialogue sequence.
- Basic arrow physics.
- Forest background music and sound effects.
- A chapter-completion trigger.

Once that demo works reliably, expand it into the 20-event campaign.

**The central design principle is to make the story playable rather than merely illustrating it.** The palace chapters should emphasize relationships and decisions, the forest chapters should emphasize exploration, Hanuman's chapters should emphasize movement and courage, and the final chapters should emphasize teamwork, conflict, and the restoration of dharma.
