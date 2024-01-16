## create two tables 
animals column1 animal_id datatype INT PRIMARY KEY
   column2 animal_name datatype VARCHAR(50)
   column3 species datatype VARCHAR(50),
   column4 habitat_id datatype  INT
## habitats 
 habitat_id INT PRIMARY KEY,
    habitat_name VARCHAR(50),
    climate VARCHAR(50)

practice group by, and sub queries , provide a list of habitata with their IDs, names, and the total number of animals in each habitat

    
CREATE TABLE animals (
	animal_id INT PRIMARY KEY, 
	animal_name VARCHAR(50),
	species VARCHAR(50),
	habitat_id INT
);

CREATE TABLE habitats (
	habitat_id INT PRIMARY KEY,
	habitat_name VARCHAR(50),
	climate VARCHAR(50)
);

INSERT INTO animals VALUES
	(1, 'lion', 'cats', 1),
	(2, 'elephant', 'marmals', 1),
	(3, 'tiger', 'cats', 2),
	(4, 'gorilla', 'monkeys', 2),
	(5, 'zebra', 'ungulate', 1),
	(6, 'polar bear', 'bears', 3),
	(7, 'bee', 'insects', 4),
	(8, 'june bug', 'insects', 4);
	
SELECT * FROM animals;

INSERT INTO habitats VALUES
	(1, 'savannah', 'hot'),
	(2, 'jungle', 'hot'),
	(3, 'polar zone', 'very cold'),
	(4, 'meadows and fields', 'temperate zone');
	
SELECT * FROM habitats;

-- Show number of animals living in colder zones

SELECT COUNT (animal_id) FROM animals
WHERE habitat_id > 2;

-- Show list of habitats with their IDs, and total number of animals in each habitat

SELECT h.habitat_id, h.habitat_name, COUNT(*) AS total_animals FROM animals a
JOIN habitats h ON a.habitat_id = h.habitat_id
GROUP BY h.habitat_id, h.habitat_name;

-- Show number of species

SELECT COUNT(animal_id), species FROM animals
GROUP BY species;
