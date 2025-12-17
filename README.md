# Wordle Game Client

Contributors: Andrew Hoang
Date: January 22, 2024

In this project the goal was to implement a client program that plays a variant of the gussing word game called Wordle. The program will make guesses for the secret word and the server will give you information about how close your guess is. Once the client guesses the correct word, it will return a secret flag to indicate that the program has run successfully.

High Level Approach:
- Implemented a TCP client with support for TLS-encrypted sockets. In addition to implementing the TCP client, JSON was used to parse and encode. Used the provided protocol to send hello, start, guess, retry and bye messages. Being able to load a list of potential words for the guessing strategy was important so that it would narrow down the secret word based on the correct letters guessed. This was done by using the server feedback about which letters were close.

Challenges Faced:
- One of the main challenges was definitely the guessing strategy. It was important that the client guesses the secret guess in less than 500 guesses, which is the limit. Another challenge was making sure that I handled the errors correctly for different failed scenarios. Also, making sure the connection is reliable and secure with the server.

Implementing Guessing Strategy:
- The initial guess would start with a common letter in order to get the most information. If the letter was right, the feedback from the server will indicate that the secret word has it and then will refine the list on potential words that it could be. Then it would make keep making guesses based on the feedback given.


Testing:
- Testing was done by running the client on TLS and non TLS to make sure that both worked and connected to the server. Also testing the the client to handle different edge cases like invalid server responses or potential network issues. Then made sure that the client could get both secret flags and made sure the socket closes after obtaining the secret flags.
 
