# Bash Commands and Games Collection - MINGW

A collection of essential bash commands and interactive command-line games.

## 📚 Essential Bash Commands Reference

### 🗺️ Navigation Commands
```bash
pwd      # Print current Working Directory
cd       # Change Directory
cd ..    # Go up one directory
cd ~     # Go to home directory
cd /     # Go to root directory
ls       # List files and directories
ls -l    # Detailed list format
ls -a    # Show hidden files
```

### 📂 File Operations
```bash
touch file.txt    # Create empty file
cat file.txt     # Display file contents
nano file.txt    # Edit file with nano editor
cp file1 file2   # Copy file1 to file2
mv file1 file2   # Move/rename file
rm file.txt      # Delete file
mkdir folder     # Create directory
rmdir folder     # Remove empty directory
rm -r folder     # Remove directory and contents
```

### 👀 File Viewing
```bash
head file.txt    # Show first 10 lines
tail file.txt    # Show last 10 lines
less file.txt    # View file with scrolling
more file.txt    # View file page by page
```

### 🔒 File Permissions
```bash
chmod +x file    # Make file executable
chmod 755 file   # Set specific permissions
chown user file  # Change file owner
```

### 💻 System Information
```bash
date             # Show current date/time
whoami          # Show current user
df -h           # Show disk space
free -h         # Show memory usage
top             # Show running processes
```

### 📝 Text Processing
```bash
grep "word" file    # Search for "word" in file
wc file            # Count lines, words, chars
sort file          # Sort lines in file
uniq file          # Remove duplicate lines
```

### 🗜️ File Compression
```bash
tar -czf archive.tar.gz files/    # Create archive
tar -xzf archive.tar.gz           # Extract archive
zip -r archive.zip files/         # Create zip
unzip archive.zip                 # Extract zip
```

### 🌐 Network
```bash
ping google.com    # Test network connection
ifconfig          # Show network interfaces
wget url          # Download file from web
curl url          # Transfer data from/to server
```

### ❓ Help Commands
```bash
man command       # Show manual for command
command --help    # Show command help
whatis command    # Brief description of command
```

### ⌨️ History and Shortcuts
```bash
history          # Show command history
!!               # Repeat last command
ctrl + c         # Stop current process
ctrl + z         # Suspend current process
clear            # Clear terminal screen
```

### 🔍 File Finding
```bash
find . -name "*.txt"    # Find all .txt files
locate filename         # Find file in database
which command          # Show command location
```

### ⚙️ Process Management
```bash
ps               # Show running processes
ps aux           # Show all processes
kill PID         # Kill process by ID
killall name     # Kill process by name
```

## 🎮 Interactive Games

### Monster Battle Game

A simple dice-rolling battle game where you face off against a monster.

#### Installation
1. Create a new file:
```bash
nano monster
```

2. Copy the game code into the file
3. Save and exit (Ctrl + X, then Y, then Enter)
4. Make it executable:
```bash
chmod +x monster
```

5. Run the game:
```bash
./monster
```

### Ancient Columbarium Game

A mystical riddle game where you search for the correct niche based on cryptic clues.

#### Installation
1. Create and navigate to the game directory:
```bash
mkdir niche-game
cd niche-game
```

2. Create the game file:
```bash
nano niche-game.sh
```

3. Copy the game code into the file
4. Save and exit (Ctrl + X, then Y, then Enter)
5. Make it executable:
```bash
chmod +x niche-game.sh
```

6. Run the game:
```bash
./niche-game.sh
```

## 🎯 Game Features

### Monster Battle
- Dice rolling combat system
- Player choice between attack and retreat
- Random number generation for battle outcomes
- Simple command-line interface

### Ancient Columbarium
- Interactive riddle-based gameplay
- Hint system with multiple levels of help
- Score tracking
- File-based niche database
- Command system for various actions
- Beautiful ASCII art interface


## 🎮 Interactive Games

### Monster Battle Game

A simple dice-rolling battle game where you face off against a monster.

#### Installation
1. Create a new file:
```bash
nano monster
```

2. Copy the game code below into the file
3. Save and exit (Ctrl + X, then Y, then Enter)
4. Make it executable:
```bash
chmod +x monster
```

5. Run the game:
```bash
./monster
```

#### Game Code
```bash
#!/bin/bash

# Function to roll dice
roll_dice() {
    echo $(( ( RANDOM % 20 ) + 1 ))
}

# Clear screen and set up game
clear

echo -e "If you have a sword, you can attack. Otherwise, you should run."

# Main game loop
while true; do
    echo -e "\nDo you want to attack? y/n"
    read choice
    
    if [ "$choice" = "y" ]; then
        echo -e "Enter a number: "
        read player_input
        
        # Roll for monster and player
        monster_roll=$(roll_dice)
        echo "The monster rolled $monster_roll"
        
        player_roll=$(roll_dice)
        echo "You rolled $player_roll"
        
        if [ $player_roll -gt $monster_roll ]; then
            echo -e "A hit! A palpable hit! You have slain the beast."
            break
        else
            echo -e "The monster strikes you! Try again!"
        fi
    elif [ "$choice" = "n" ]; then
        echo -e "You run away to fight another day!"
        break
    else
        echo "Please enter y or n"
    fi
done
```

### Ancient Columbarium Game

A mystical riddle game where you search for the correct niche based on cryptic clues.

#### Installation
1. Create and navigate to the game directory:
```bash
mkdir niche-game
cd niche-game
```

2. Create the game file:
```bash
nano niche-game.sh
```

3. Copy the game code below into the file
4. Save and exit (Ctrl + X, then Y, then Enter)
5. Make it executable:
```bash
chmod +x niche-game.sh
```

6. Run the game:
```bash
./niche-game.sh
```

#### Game Code
```bash
#!/bin/bash

# Create the niches data file
cat > niches << 'EOL'
23 Eagle
05 Dove
12 Lotus flower
19 Sword wreathed in flame
27 Mountain
04 Book
16 Tree branch
09 Sun
01 Musical notes
22 Pine tree
10 An elder god
15 Amulet
29 Sea monster
07 Crescent moon
25 Butterfly
18 Cross
14 A familiar constellation
30 Flame and candle
20 Goblet
08 Winged warrior
11 Water droplet
17 Castle
03 Ibis
24 Rose
28 Hammer
21 Full moon
02 Anchor
26 Wheat sheaf
13 Crest of an ancient noble family
06 Heart
EOL

# Initialize game variables
score=0
attempts=3
target_niche=""
hint_count=0

# Function to display welcome message
display_welcome() {
    echo "Welcome to the Ancient Columbarium"
    echo "===================================="
    echo "Before you stands an ancient wall of niches,"
    echo "each marked with mystical symbols."
    echo "Find the right niche to reveal its secrets..."
    echo
}

# Function to generate a random riddle
generate_riddle() {
    riddles=(
        "I soar high above, king of the skies|23"
        "Peace I bring on wings of white|05"
        "In sacred waters I bloom with grace|12"
        "By flame empowered, I cut through night|19"
        "Silent guardian, reaching to sky|27"
        "Knowledge bound in leather and page|04"
        "From earth I stretch toward heaven's light|16"
        "Center of all, I give you day|09"
        "Without words I speak in tone|01"
        "Ever green, pointing to stars|22"
        "Ancient one from depths unknown|10"
        "Around the neck, protection found|15"
        "In depths I swim, terror below|29"
        "Night's eye in partial gleam|07"
        "On wings of beauty, transformation|25"
        "Where paths meet, salvation found|18"
        "In stars I tell an ancient tale|14"
        "Light in darkness, wax and wick|30"
        "Holy vessel, filled with life|20"
        "Heaven's soldier, sword in hand|08"
        "Life-giving tear from sky to earth|11"
        "Stone fortress, safety within|17"
        "Sacred bird of ancient scrolls|03"
        "Love's flower, thorns below|24"
        "Tool of gods and mortal men|28"
        "Night's eye in complete display|21"
        "Holds fast in storm and calm|02"
        "Golden harvest, staff of life|26"
        "Blood and honor, time-worn seal|13"
        "Life's rhythm beats within|06"
    )
    
    random_index=$((RANDOM % ${#riddles[@]}))
    IFS='|' read -r riddle answer <<< "${riddles[$random_index]}"
    target_niche=$answer
    echo "$riddle"
}

# Function to provide a hint
provide_hint() {
    if [ $hint_count -lt 3 ]; then
        case $hint_count in
            0)
                echo "Hint: Look for niche number $target_niche"
                ;;
            1)
                symbol=$(grep "^$target_niche " niches | cut -d' ' -f2-)
                echo "Hint: The symbol you seek is: $symbol"
                ;;
            2)
                echo "Hint: You can use 'grep' to search the niches!"
                echo "Try: grep \"<symbol>\" niches"
                ;;
        esac
        hint_count=$((hint_count + 1))
    else
        echo "No more hints available!"
    fi
}

# Function to check guess
check_guess() {
    local guess=$1
    if [ "$guess" = "$target_niche" ]; then
        echo "The niche glows with an otherworldly light!"
        echo "You have chosen wisely!"
        score=$((score + 1))
        return 0
    else
        echo "The niche remains dark. Try again."
        attempts=$((attempts - 1))
        return 1
    fi
}

# Main game loop
display_welcome

while [ $attempts -gt 0 ]; do
    echo
    echo "Attempts remaining: $attempts | Score: $score"
    echo "------------------------"
    echo "A riddle appears before you:"
    echo
    riddle=$(generate_riddle)
    echo "$riddle"
    echo
    echo "Commands:"
    echo "  guess <number> - Try a niche number"
    echo "  hint          - Get a hint (3 available)"
    echo "  list          - Show all niches"
    echo "  quit          - Exit the game"
    echo
    
    read -p "What would you like to do? " action number
    
    case $action in
        guess)
            if [[ ! $number =~ ^[0-9]+$ ]]; then
                echo "Please enter a valid niche number"
                continue
            fi
            check_guess $number
            if [ $? -eq 0 ]; then
                generate_riddle
            fi
            if [ $attempts -eq 0 ]; then
                echo "Game Over! Final score: $score"
                exit 0
            fi
            ;;
        hint)
            provide_hint
            ;;
        list)
            cat niches
            ;;
        quit)
            echo "Thanks for playing! Final score: $score"
            exit 0
            ;;
        *)
            echo "Invalid command. Try again."
            ;;
    esac
done
```

## 🎯 Game Features

### Monster Battle
- Simple dice-rolling combat system
- Player choice between attack and retreat
- Random number generation (1-20) for battle outcomes
- Turn-based combat mechanics
- Clear win/lose conditions

### Ancient Columbarium
- Interactive riddle-based gameplay
- 30 unique riddles and symbols
- 3-tier hint system
- Score tracking
- File-based niche database
- Multiple commands: guess, hint, list, quit
- Persistent game state
- Error handling for invalid inputs

## 📝 Command Quick Reference

### Monster Battle Commands
```bash
y     # Choose to attack the monster
n     # Choose to run away
```

### Ancient Columbarium Commands
```bash
guess <number>    # Try to guess a niche number
hint              # Get a hint (3 available per riddle)
list              # Show all niches and their symbols
quit              # Exit the game
```

## 🔧 Installation Requirements

- Bash shell environment
- Basic command line knowledge
- File system write permissions
- `nano` text editor (or any other text editor)

## 🤝 Contributing

Feel free to fork this repository and submit pull requests for:
- New bash commands and examples
- Game improvements or bug fixes
- Additional command-line games
- Documentation improvements
- New riddles or game features

## 🐛 Troubleshooting

If you encounter issues:
1. Ensure files have executable permissions (`chmod +x`)
2. Check that files use Unix line endings (LF, not CRLF)
3. Verify Bash is installed (`bash --version`)
4. Make sure the niches file is created correctly

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.
