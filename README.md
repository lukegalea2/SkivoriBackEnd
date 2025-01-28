# SkivoriBackEnd

Welcome to my Skivori Test,

To install this project locally, please download both the SkivoriBackend and the SkivoriFrontEnd Files.

Once installed please run 'npm install' on both files, this will install all the packages needed to run the project.

To start running the backend, run 'npm start' on your terminal, the backend will start running on port:8080.

To start running the frontend, run 'npm run dev' on your terminal which will start running on port:3000.

Access the front end from http://localhost:3000/.

Question 1: Will be clearly displayed once the front end is loaded. Question 2: Type anything in the search bar for results. Question 3: Click on 'Play a game' on the header to start the spinning game. Question 4: Middleware was added and marked in the backend code. Question 5: Optimisation was made on the frontend code - Instead of on every keystroke, the API is called after a small amount of time that the user stops typing. Question 6: To see the conversion, please click on the coins indication on the header. Question 7: The Scheme for the database can be found as an image in the repository. (DBScheme.png)

This is the SQL Code:

CREATE TABLE game_types ( id INT PRIMARY KEY AUTO_INCREMENT, type_name VARCHAR(255) NOT NULL );

CREATE TABLE countries ( id INT PRIMARY KEY AUTO_INCREMENT, country_name VARCHAR(255) NOT NULL );

CREATE TABLE games ( id INT PRIMARY KEY AUTO_INCREMENT, name VARCHAR(255) NOT NULL, game_type_id INT NOT NULL, created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP, FOREIGN KEY (game_type_id) REFERENCES game_types(id) );

CREATE TABLE game_country ( game_id INT NOT NULL, country_id INT NOT NULL, PRIMARY KEY (game_id, country_id), FOREIGN KEY (game_id) REFERENCES games(id), FOREIGN KEY (country_id) REFERENCES countries(id) );

CREATE TABLE players ( id INT PRIMARY KEY AUTO_INCREMENT, username VARCHAR(255) NOT NULL UNIQUE, email VARCHAR(255) NOT NULL, created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP, updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP );

CREATE TABLE favorites ( player_id INT NOT NULL, game_id INT NOT NULL, PRIMARY KEY (player_id), FOREIGN KEY (player_id) REFERENCES players(id), FOREIGN KEY (game_id) REFERENCES games(id) );

CREATE TABLE spins ( id INT PRIMARY KEY AUTO_INCREMENT, player_id INT NOT NULL, game_id INT NOT NULL, amount_won_lost DECIMAL(10, 2) NOT NULL, -- Amount can be negative if the player loses money spin_time TIMESTAMP DEFAULT CURRENT_TIMESTAMP, FOREIGN KEY (player_id) REFERENCES players(id), FOREIGN KEY (game_id) REFERENCES games(id) );

Question 8:

In terms of AI, I used chatGPT to guide me in some instances. I used it to create the optimal solution for me to create the scoring system for the spin game. I felt like the solution that I had was not as clean so I asked chatGpt to optimize my solution.

Another instance where I used chatGPT was for the middleware question. As I don't feel like I have enough experience when it comes to middleware I used it to give me ideas and show me how I can implement them. I used this as a learning experience rather than copying and pasting from the editor.

The last instance where I used chatGPT was in the DB Scheme. After designing my own, I asked chatGPT to create one for me to check if mine was correct. My implementation was correct however I had a 2 missing relationships which I added with the help of chatGPT.

