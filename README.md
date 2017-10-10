# CardGame

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CardDeck
{
    enum Suit
    {
        Heart,
        Diamond,
        Spade,
        Club
    }
; class Program
    {
        static void Main()
        {
            Console.WriteLine("Welcome to the card game?");
            Console.WriteLine("Press enter to draw your hand");
            Console.ReadKey();


            Deck myDeck = new Deck();

//checking to see if it works

            List<Card> shuffleDeck = new List<Card>();
            Random r = new Random();
            int p = 0;
            while (myDeck.Cards.Count > 0)
            {
                p = r.Next(0, myDeck.Cards.Count);
                shuffleDeck.Add(myDeck.Cards[p]);
                myDeck.Cards.Remove(myDeck.Cards[p]);
            }
            myDeck.Cards = shuffleDeck;

            foreach (Card x in myDeck.Cards)
            {
                Console.WriteLine(x.value + " of " + x.suit + "s\n");
            }

            Console.ReadLine();


        }
    }

    class Card
    {
       

        public string value { get; set; }

        public Suit suit { get; set; }
      
     

        public Card(Suit s, string v)
        {
            
            suit = s;
            value = v;

        }
    }

    class Deck
    {
        public List<Card> Cards { get; set; }
        public List<Card> DiscardPile { get; set; }

        DiscardPile = new List<Card>();


        public Deck()
        {
            Cards = new List<Card>();
            

            foreach (Suit suit in Enum.GetValues(typeof(Suit)))
            {
                for (int x = 1; x <= 13; x++)
                {
                    
                    switch (x)
                    {
                        case 1:
                            Cards.Add(new Card(suit, "A"));
                            break;
                        case 11:
                            Cards.Add(new Card(suit, "J"));
                            break;
                        case 12:
                            Cards.Add(new Card(suit, "Q"));
                            break;
                        case 13:
                            Cards.Add(new Card(suit, "K"));
                            break;
                        default:
                            Cards.Add(new Card(suit, x.ToString()));
                            break;
                    }
                   
                }
            }
        }
    }
}
