# ANADA-# Function to generate a shuffled deck of cards
def create_deck():
    suits = ['Hearts', 'Diamonds', 'Clubs', 'Spades']
    ranks = ['2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K', 'A']
    deck = [(rank, suit) for suit in suits for rank in ranks]
    random.shuffle(deck)
    return deck

# Function to deal three cards to each player
def deal_cards(deck):
    player_hand = deck[:3]
    computer_hand = deck[3:6]
    return player_hand, computer_hand

# Function to evaluate the rank of a hand
def evaluate_hand(hand):
    values = {'2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9, '10': 10, 'J': 11, 'Q': 12, 'K': 13, 'A': 14}
    hand_values = sorted([values[card[0]] for card in hand], reverse=True)
    return hand_values

# Function to compare two hands and determine the winner
def compare_hands(player_hand, computer_hand):
    player_values = evaluate_hand(player_hand)
    computer_values = evaluate_hand(computer_hand)
    
    if player_values > computer_values:
        return "Player wins!"
    elif player_values < computer_values:
        return "Computer wins!"
    else:
        return "It's a tie!"

# Function to display the hands
def show_hand(hand, owner="Player"):
    print(f"{owner}'s hand: ", end="")
    for card in hand:
        print(f"{card[0]} of {card[1]}", end="; ")
    print("\n")

# Main game function
def play_teen_patti():
    deck = create_deck()
    player_hand, computer_hand = deal_cards(deck)
    
    print("Welcome to Teen Patti!")
    
    show_hand(player_hand, "Player")
    
    input("Press Enter to reveal the computer's hand...")
    
    show_hand(computer_hand, "Computer")
    
    result = compare_hands(player_hand, computer_hand)
    print(result)

# Run the game
if __name__ == "__main__":
    play_teen_patti()
