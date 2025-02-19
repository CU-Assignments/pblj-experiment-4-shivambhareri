import java.util.*;

class CardCollection {
    private List<String> cards;

    public CardCollection() {
        cards = new ArrayList<>();
    }

    public void addCard(String card) {
        cards.add(card);
    }

    public List<String> getCardsBySymbol(String symbol) {
        List<String> matchedCards = new ArrayList<>();
        for (String card : cards) {
            if (card.contains(symbol)) {
                matchedCards.add(card);
            }
        }
        return matchedCards;
    }

    public void displayCards() {
        System.out.println("All Cards: " + cards);
    }

    public static void main(String[] args) {
        CardCollection collection = new CardCollection();

        collection.addCard("Heart - Ace");
        collection.addCard("Heart - King");
        collection.addCard("Spade - Queen");
        collection.addCard("Diamond - 10");
        collection.addCard("Club - Jack");

        collection.displayCards();

        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter a symbol to search (Heart, Spade, Diamond, Club): ");
        String symbol = scanner.nextLine();

        List<String> foundCards = collection.getCardsBySymbol(symbol);

        if (!foundCards.isEmpty()) {
            System.out.println("Cards found: " + foundCards);
        } else {
            System.out.println("No cards found with symbol: " + symbol);
        }

        scanner.close();
    }
}
