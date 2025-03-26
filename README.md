# Scratch
Space Explore Adventure
# Scratch Project Idea: "Space Explorer Adventure"

I'll outline a fun space-themed game that meets all your requirements while being engaging but not overly complex.

## Concept Overview
"Space Explorer Adventure" is a game where the player controls a spaceship sprite to collect stars while avoiding asteroids. The player earns points for each star collected and loses health when hitting asteroids.

## Requirements Implementation

### 1. Sprites
- **Spaceship** (non-cat sprite): Player-controlled character
- **Asteroid**: Obstacles to avoid
- **Star**: Collectible items

### 2. Scripts
1. Spaceship control script (arrow key movement)
2. Asteroid generation and movement script
3. Star collection and scoring script
4. Health tracking script
5. Custom block for explosion animation

### 3. Programming Elements
- **Conditional**: If spaceship touches asteroid, decrease health
- **Loop**: Forever loop for asteroid generation
- **Variable**: Score and Health variables

### 4. Custom Block
- "Create explosion" block that takes position (x,y) as input and shows an explosion animation

## Step-by-Step Implementation

### 1. Setup
1. Create new Scratch project
2. Delete the cat sprite
3. Add spaceship sprite (from Scratch library or draw your own)
4. Add asteroid and star sprites

### 2. Variables
1. Create variables:
   - "Score" (for stars collected)
   - "Health" (starts at 100)
   - "GameSpeed" (controls difficulty)

### 3. Spaceship Code
```scratch
when green flag clicked
set [Health v] to (100)
set [Score v] to (0)
forever
  if <key [left arrow v] pressed?> then
    change x by (-10)
  end
  if <key [right arrow v] pressed?> then
    change x by (10)
  end
  if <key [up arrow v] pressed?> then
    change y by (10)
  end
  if <key [down arrow v] pressed?> then
    change y by (-10)
  end
end
```

### 4. Asteroid Code
```scratch
when green flag clicked
forever
  create clone of [myself v]
  wait (pick random (1) to (3)) seconds
end

when I start as a clone
go to x: (pick random (-240) to (240)) y: (180)
show
repeat until <touching [edge v]?>
  change y by (-5)
  if <touching [Spaceship v]?> then
    change [Health v] by (-10)
    Create Explosion at x: (x position) y: (y position) :: custom
    delete this clone
  end
end
delete this clone
```

### 5. Star Code
```scratch
when green flag clicked
forever
  go to x: (pick random (-240) to (240)) y: (pick random (-180) to (180))
  wait (pick random (2) to (5)) seconds
end

when green flag clicked
forever
  if <touching [Spaceship v]?> then
    change [Score v] by (10)
    play sound [collect v]
    go to x: (pick random (-240) to (240)) y: (pick random (-180) to (180))
  end
end
```

### 6. Custom Block: Create Explosion
```scratch
define Create Explosion at x: (x) y: (y)
go to x: (x) y: (y)
show
switch costume to [explosion1 v]
play sound [explosion v]
wait (0.1) seconds
switch costume to [explosion2 v]
wait (0.1) seconds
switch costume to [explosion3 v]
wait (0.1) seconds
hide
```

### 7. Game Over Check
```scratch
when green flag clicked
forever
  if <(Health) < [1]> then
    say [Game Over! Final Score: ] for (2) seconds
    say (join [Score: ] (Score)) for (2) seconds
    stop [all v]
  end
end
```

## Enhancements (Optional)
1. Add different types of asteroids (some move faster)
2. Include power-ups that temporarily increase speed or invincibility
3. Add levels that increase difficulty by changing GameSpeed
4. Include a timer for time-based challenges

## Testing Strategy
1. Test spaceship movement controls
2. Verify star collection increases score
3. Check that asteroid collisions reduce health
4. Confirm game over triggers when health reaches 0
5. Test explosion animation appears at correct locations

This project meets all requirements while being fun to play and not overly complex. The custom block provides good abstraction for the explosion effect, and the multiple sprites interact in clear ways. The game has clear win/lose conditions and provides immediate feedback to the player.
