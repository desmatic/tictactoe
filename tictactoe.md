You are an expert software engineer specializing in front-end development with Next.js and React.

Your task is to create a complete, functional Tic Tac Toe game application using Next.js, Tailwind CSS, and plain JavaScript. Please follow these requirements carefully.

**Project Requirements:**

1.  **Framework**: Use Next.js with the App Router.
2.  **Language**: Use plain ES6 JavaScript (no TypeScript). Replace CommonJs syntax with EcmaScript import/export syntax.
3.  **Styling**: Use Tailwind CSS for all styling. The design should be clean, modern, responsive, and accessibility-friendly. Use utility classes directly in your JSX. Assume the game will be used on a tablet or mobile and take up the entire screen.

**Game Logic and Features:**

1.  **Game Board**: Display a 3x3 grid of clickable squares.
2.  **Players**: The game is for two players, 'X' and 'O'. 'X' always starts.
3.  **Turns**: Players alternate turns. Clicking an empty square places the current player's mark. A square cannot be clicked more than once.
4.  **State Management**: Use React's `useState` hook to manage all game state, including the board's squares, the current player, and the game's status.
5.  **Win Condition**: The application must correctly detect when a player has won by placing three of their marks in a horizontal, vertical, or diagonal row.
6.  **Draw Condition**: The game must detect a draw if all squares on the board are filled and no winner has been declared.
7.  **Status Display**: A status message must be clearly visible, indicating:
    *   Whose turn is next (e.g., "Next player: X").
    *   Who won the game (e.g., "Winner: O").
    *   If the game is a draw (e.g., "It's a draw!").
8.  **Game Over**: Once a player wins or the game is a draw, no more moves should be possible until the game is reset.
9.  **Reset Game**: Provide a "Play Again" button that resets the game to its initial state, allowing for a new game to be played.

**Component and File Structure:**

Please organize the code into the following structure and provide the complete code for each file.

*   `tailwind.config.js`: The configuration file for Tailwind CSS.
*   `postcss.config.js`: The configuration file for PostCSS.
*   `app/layout.js`: The root layout, which should import `globals.css`.
*   `app/globals.css`: The global stylesheet, containing the Tailwind CSS directives.
*   `app/page.js`: The main entry point for the application, which will host the `Game` component.
*   `components/Game.js`: The main parent component that holds the game state and logic. This must be a client component (`'use client'`).
*   `components/Board.js`: A component that renders the 3x3 grid of squares.
*   `components/Square.js`: A reusable component that represents a single clickable square on the board.

**Code Quality:**

*   The code should be clean, well-commented, and easy to understand.
*   Follow React best practices, such as lifting state up and using props for communication.
*   Use ES6 features where appropriate.

Please provide the complete code for each file.
