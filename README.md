# Bancos de dados NoSQL: Atividade Prática – Neo4j

### Exercise 1: Retrieving Nodes (Preparations)

```
    Added 171 labels, created 171 nodes, set 564 properties, created 253 relationships, completed after 56 ms.
```

### Exercise 1.1: Retrieve all nodes from the database (Solution)

```
    MATCH (n) RETURN n

    [
        {
            "n": {
            "identity": 0,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Matrix",
                "tagline": "Welcome to the Real World",
                "released": 1999
            }
            }
        },
        {
            "n": {
            "identity": 1,
            "labels": [
                "Person"
            ],
            "properties": {
                "name": "Keanu Reeves",
                "born": 1964
            }
            }
        },
        {
            "n": {
            "identity": 2,
            "labels": [
                "Person"
            ],
            "properties": {
                "name": "Carrie-Anne Moss",
                "born": 1967
            }
            }
        }
    ]
```

### Exercise 1.2: Examine the schema of your database (Solution)

```
    CALL db.schema.visualization

    [
        {
            "nodes": [
            {
                "identity": -9,
                "labels": [
                "Movie"
                ],
                "properties": {
                "indexes": [],
                "name": "Movie",
                "constraints": []
                }
            },
            {
                "identity": -10,
                "labels": [
                "Person"
                ],
                "properties": {
                "indexes": [],
                "name": "Person",
                "constraints": []
                }
            }
            ]
        }
    ]
```

### Exercise 1.3: Retrieve all Person nodes (Instructions)

```
    MATCH (p:Person) RETURN p

    [
        {
            "p": {
            "identity": 1,
            "labels": [
                "Person"
            ],
            "properties": {
                "name": "Keanu Reeves",
                "born": 1964
            }
            }
        },
        {
            "p": {
            "identity": 2,
            "labels": [
                "Person"
            ],
            "properties": {
                "name": "Carrie-Anne Moss",
                "born": 1967
            }
            }
        },
        {
            "p": {
            "identity": 3,
            "labels": [
                "Person"
            ],
            "properties": {
                "name": "Laurence Fishburne",
                "born": 1961
            }
            }
        },
        {
            "p": {
            "identity": 4,
            "labels": [
                "Person"
            ],
            "properties": {
                "name": "Hugo Weaving",
                "born": 1960
            }
            }
        }
    ]
```

### Exercise 1.4: Retrieve all Movie nodes (Instructions)

```
    MATCH (m:Movie) RETURN m

    [
        {
            "m": {
            "identity": 0,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Matrix",
                "tagline": "Welcome to the Real World",
                "released": 1999
            }
            }
        },
        {
            "m": {
            "identity": 9,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Matrix Reloaded",
                "tagline": "Free your mind",
                "released": 2003
            }
            }
        },
        {
            "m": {
            "identity": 10,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Matrix Revolutions",
                "tagline": "Everything that has a beginning has an end",
                "released": 2003
            }
            }
        },
        {
            "m": {
            "identity": 11,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Devil's Advocate",
                "tagline": "Evil has its winning ways",
                "released": 1997
            }
            }
        }
    ]
```

### Exercise 2.1: Retrieve all movies that were released in a specific year (Instructions)

```
    MATCH (m:Movie {released:2003}) RETURN m

    ![Exercise 2.1](graph2.1.png)
```


### Exercise 2.2: View the retrieved results as a table (Solution)

```
    [
        {
            "m": {
            "identity": 9,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Matrix Reloaded",
                "tagline": "Free your mind",
                "released": 2003
            }
            }
        },
        {
            "m": {
            "identity": 10,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "The Matrix Revolutions",
                "tagline": "Everything that has a beginning has an end",
                "released": 2003
            }
            }
        },
        {
            "m": {
            "identity": 154,
            "labels": [
                "Movie"
            ],
            "properties": {
                "title": "Something's Gotta Give",
                "released": 2003
            }
            }
        }
    ]
```

### Exercise 2.3: Query the database for all property keys (Solution)

```
    CALL db.propertyKeys

    [
        {
            "propertyKey": "tagline"
        },
        {
            "propertyKey": "title"
        },
        {
            "propertyKey": "released"
        },
        {
            "propertyKey": "born"
        },
        {
            "propertyKey": "name"
        },
        {
            "propertyKey": "roles"
        },
        {
            "propertyKey": "summary"
        },
        {
            "propertyKey": "rating"
        }
    ]
```

### Exercise 2.4: Retrieve all Movies released in a specific year, returning their titles (Solution)

```
    MATCH (m:Movie {released: 2006}) RETURN m.title

    [
        {
            "m.title": "RescueDawn"
        },
        {
            "m.title": "The Da Vinci Code"
        },
        {
            "m.title": "V for Vendetta"
        },
        {
            "m.title": "RescueDawn"
        },
        {
            "m.title": "The Da Vinci Code"
        },
        {
            "m.title": "V for Vendetta"
        }
    ]
```

### Exercise 2.5: Display title, released, and tagline values for every Movie node in the graph (Solution

```
    MATCH (m:Movie) RETURN m.title, m.released, m.tagline

    [
        {
            "m.title": "The Matrix",
            "m.released": 1999,
            "m.tagline": "Welcome to the Real World"
        },
        {
            "m.title": "The Matrix Reloaded",
            "m.released": 2003,
            "m.tagline": "Free your mind"
        },
        {
            "m.title": "The Matrix Revolutions",
            "m.released": 2003,
            "m.tagline": "Everything that has a beginning has an end"
        },
        {
            "m.title": "The Devil's Advocate",
            "m.released": 1997,
            "m.tagline": "Evil has its winning ways"
        }
    ]
```

### Exercise 2.6: Display more user-friendly headers in the table (Solution)

```
    MATCH (m:Movie) RETURN m.title AS `movie title`, m.released AS released, m.tagline AS tagLine

    [
        {
            "Movie Title": "The Matrix",
            "released": 1999,
            "tagline": "Welcome to the Real World"
        },
        {
            "Movie Title": "The Matrix Reloaded",
            "released": 2003,
            "tagline": "Free your mind"
        },
        {
            "Movie Title": "The Matrix Revolutions",
            "released": 2003,
            "tagline": "Everything that has a beginning has an end"
        },
        {
            "Movie Title": "The Devil's Advocate",
            "released": 1997,
            "tagline": "Evil has its winning ways"
        },
        {
            "Movie Title": "A Few Good Men",
            "released": 1992,
            "tagline": "In the heart of the nation's capital, in a courthouse of the U.S. government, one man will stop at nothing to keep his honor, and one will stop at nothing to find the truth."
        }
    ]    
```

### Exercise 3.1: Display the schema of the database (Instructions)

```
    CALL db.schema.visualization

    ![Exercise 3.1](graph3.1.png)
```

### Exercise 3.2: Retrieve all people who wrote the movie Speed Racer (Solution)

```
    MATCH (p:Person)-[:WROTE]->(:Movie {title: 'Speed Racer'}) RETURN p.name

    [
        {
            "p.name": "Lana Wachowski"
        },
        {
            "p.name": "Lilly Wachowski"
        },
        {
            "p.name": "Lilly Wachowski"
        },
        {
            "p.name": "Lana Wachowski"
        }
    ]    
```

### Exercise 3.3: Retrieve all movies that are connected to the person, Tom Hanks (Solution)

```
    MATCH (m:Movie)<--(:Person {name: 'Tom Hanks'}) RETURN m.title

    [
        {
            "m.title": "A League of Their Own"
        },
        {
            "m.title": "Cloud Atlas"
        },
        {
            "m.title": "The Da Vinci Code"
        },
        {
            "m.title": "Sleepless in Seattle"
        },
        {
            "m.title": "The Polar Express"
        },
        {
            "m.title": "The Green Mile"
        },
        {
            "m.title": "Cast Away"
        },
        {
            "m.title": "Charlie Wilson's War"
        },
        {
            "m.title": "That Thing You Do"
        },
        {
            "m.title": "That Thing You Do"
        },
        {
            "m.title": "Joe Versus the Volcano"
        },
        {
            "m.title": "Apollo 13"
        },
        {
            "m.title": "You've Got Mail"
        },
        {
            "m.title": "Cast Away"
        },
        {
            "m.title": "Joe Versus the Volcano"
        },
        {
            "m.title": "Cloud Atlas"
        },
        {
            "m.title": "That Thing You Do"
        },
        {
            "m.title": "The Green Mile"
        },
        {
            "m.title": "Apollo 13"
        },
        {
            "m.title": "Sleepless in Seattle"
        },
        {
            "m.title": "Charlie Wilson's War"
        },
        {
            "m.title": "A League of Their Own"
        },
        {
            "m.title": "That Thing You Do"
        },
        {
            "m.title": "The Da Vinci Code"
        },
        {
            "m.title": "You've Got Mail"
        },
        {
            "m.title": "The Polar Express"
        }
    ]
```

### Exercise 3.4: Retrieve information about the relationships Tom Hanks has with the set of movies retrieved earlier (Solution)

```
    MATCH (m:Movie)-[rel]-(:Person {name: 'Tom Hanks'}) RETURN m.title, type(rel)

    [
        {
            "m.title": "A League of Their Own",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "Cloud Atlas",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "The Da Vinci Code",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "Sleepless in Seattle",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "The Polar Express",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "The Green Mile",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "Cast Away",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "Charlie Wilson's War",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "That Thing You Do",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "That Thing You Do",
            "type(rel)": "DIRECTED"
        },
        {
            "m.title": "Joe Versus the Volcano",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "Apollo 13",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "You've Got Mail",
            "type(rel)": "ACTED_IN"
        },
        {
            "m.title": "Cast Away",
            "type(rel)": "ACTED_IN"
        }   
    ]
```

### Exercise 3.5: Retrieve information about the roles that Tom Hanks acted in (Solution)

```
    MATCH (m:Movie)-[rel:ACTED_IN]-(:Person {name: 'Tom Hanks'}) RETURN m.title, rel.roles

    [
        {
            "m.title": "A League of Their Own",
            "rel.roles": [
            "Jimmy Dugan"
            ]
        },
        {
            "m.title": "Cloud Atlas",
            "rel.roles": [
            "Zachry",
            "Dr. Henry Goose",
            "Isaac Sachs",
            "Dermot Hoggins"
            ]
        },
        {
            "m.title": "The Da Vinci Code",
            "rel.roles": [
            "Dr. Robert Langdon"
            ]
        },
        {
            "m.title": "Sleepless in Seattle",
            "rel.roles": [
            "Sam Baldwin"
            ]
        }
    ]
```

### Exercise 4.1: Retrieve all movies that Tom Cruise acted in (Solution)

```
    MATCH (a:Person)-[:ACTED_IN]->(m:Movie)
    WHERE a.name = 'Tom Cruise'
    RETURN m.title as Movie

    [
        {
            "Movie": "Jerry Maguire"
        },
        {
            "Movie": "Top Gun"
        },
        {
            "Movie": "A Few Good Men"
        },
        {
            "Movie": "Top Gun"
        },
        {
            "Movie": "Jerry Maguire"
        },
        {
            "Movie": "A Few Good Men"
        }
    ]
```

### Exercise 4.2: Retrieve all people that were born in the 70’s (Solution)

```
    MATCH (a:Person)
    WHERE a.born >= 1970 AND a.born < 1980
    RETURN a.name as Name, a.born as `Year Born`

    [
        {
            "Name": "Emil Eifrem",
            "Years Born": 1978
        },
        {
            "Name": "Charlize Theron",
            "Years Born": 1975
        },
        {
            "Name": "Noah Wyle",
            "Years Born": 1971
        },
        {
            "Name": "Jerry O'Connell",
            "Years Born": 1974
        },
        {
            "Name": "Jay Mohr",
            "Years Born": 1970
        },
        {
            "Name": "Regina King",
            "Years Born": 1971
        },
        {
            "Name": "River Phoenix",
            "Years Born": 1970
        },
        {
            "Name": "Corey Feldman",
            "Years Born": 1971
        }
    ]
```

### Exercise 4.3: Retrieve the actors who acted in the movie The Matrix who were born after 1960 (Solution)

```
    MATCH (a:Person)-[:ACTED_IN]->(m:Movie)
    WHERE a.born > 1960 AND m.title = 'The Matrix'
    RETURN a.name as Name, a.born as `Year Born`

    [
        {
            "Name": "Emil Eifrem",
            "Years Born": 1978
        },
        {
            "Name": "Laurence Fishburne",
            "Years Born": 1961
        },
        {
            "Name": "Carrie-Anne Moss",
            "Years Born": 1967
        },
        {
            "Name": "Keanu Reeves",
            "Years Born": 1964
        },
        {
            "Name": "Keanu Reeves",
            "Years Born": 1964
        },
        {
            "Name": "Emil Eifrem",
            "Years Born": 1978
        },
        {
            "Name": "Laurence Fishburne",
            "Years Born": 1961
        },
        {
            "Name": "Carrie-Anne Moss",
            "Years Born": 1967
        }
    ]
```

### Exercise 4.4: Retrieve all movies by testing the node label and a property (Solution)

```
    MATCH (m)
    WHERE m:Movie AND m.released = 2000
    RETURN m.title

    [
        {
            "m.title": "Jerry Maguire"
        },
        {
            "m.title": "The Replacements"
        },
        {
            "m.title": "Cast Away"
        },
        {
            "m.title": "Jerry Maguire"
        },
        {
            "m.title": "The Replacements"
        },
        {
            "m.title": "Cast Away"
        }
    ]
```

### Exercise 4.5: Retrieve all people that wrote movies by testing the relationship between two nodes (Solution)

```
    MATCH (a)-[rel]->(m)
    WHERE a:Person AND type(rel) = 'WROTE' AND m:Movie
    RETURN a.name as Name, m.title as Movie

    [
        {
            "Name": "Aaron Sorkin",
            "Movie": "A Few Good Men"
        },
        {
            "Name": "Jim Cash",
            "Movie": "Top Gun"
        },
        {
            "Name": "Cameron Crowe",
            "Movie": "Jerry Maguire"
        },
        {
            "Name": "Nora Ephron",
            "Movie": "When Harry Met Sally"
        },
        {
            "Name": "David Mitchell",
            "Movie": "Cloud Atlas"
        },
        {
            "Name": "Lana Wachowski",
            "Movie": "V for Vendetta"
        },
        {
            "Name": "Lilly Wachowski",
            "Movie": "V for Vendetta"
        },
        {
            "Name": "Lana Wachowski",
            "Movie": "Speed Racer"
        }
    ]
```

### Exercise 4.6: Retrieve all people in the graph that do not have a property (Solution)

```
    MATCH (a:Person)
    WHERE NOT exists(a.born)
    RETURN a.name as Name

    [
        {
            "Name": "Naomie Harris"
        },
        {
            "Name": "Paul Blythe"
        },
        {
            "Name": "Angela Scope"
        },
        {
            "Name": "Jessica Thompson"
        },
        {
            "Name": "James Thompson"
        },
        {
            "Name": "Naomie Harris"
        },
        {
            "Name": "Paul Blythe"
        },
        {
            "Name": "Angela Scope"
        },
        {
            "Name": "Jessica Thompson"
        },
        {
            "Name": "James Thompson"
        }
    ]
```

### Exercise 4.7: Retrieve all people related to movies where the relationship has a property (Solution)

```
    MATCH (a:Person)-[rel]->(m:Movie)
    WHERE exists(rel.rating)
    RETURN a.name as Name, m.title as Movie, rel.rating as Rating

    [
        {
            "Name": "Jessica Thompson",
            "Movie": "Jerry Maguire",
            "Rating": 92
        },
        {
            "Name": "Angela Scope",
            "Movie": "The Replacements",
            "Rating": 62
        },
        {
            "Name": "James Thompson",
            "Movie": "The Replacements",
            "Rating": 100
        },
        {
            "Name": "Jessica Thompson",
            "Movie": "The Replacements",
            "Rating": 65
        },
        {
            "Name": "Jessica Thompson",
            "Movie": "The Birdcage",
            "Rating": 45
        },
        {
            "Name": "Jessica Thompson",
            "Movie": "Unforgiven",
            "Rating": 85
        },
        {
            "Name": "Jessica Thompson",
            "Movie": "Cloud Atlas",
            "Rating": 95
        },
        {
            "Name": "James Thompson",
            "Movie": "The Da Vinci Code",
            "Rating": 65
        },
        {
            "Name": "Jessica Thompson",
            "Movie": "The Da Vinci Code",
            "Rating": 68
        }
    ]
```

### Exercise 4.8: Retrieve all actors whose name begins with James (Solution)

```
    MATCH (a:Person)-[:ACTED_IN]->(:Movie)
    WHERE a.name STARTS WITH 'James'
    RETURN a.name

    [
        {
            "Name": "James Marshall"
        },
        {
            "Name": "James Cromwell"
        },
        {
            "Name": "James Cromwell"
        },
        {
            "Name": "James Marshall"
        },
        {
            "Name": "James Cromwell"
        },
        {
            "Name": "James Cromwell"
        }
    ]
```

### Exercise 4.9: Retrieve all REVIEWED relationships from the graph with filtered results (Solution)

```
    MATCH (:Person)-[r:REVIEWED]->(m:Movie)
    WHERE toLower(r.summary) CONTAINS 'fun'
    RETURN  m.title as Movie, r.summary as Review, r.rating as Rating

    [
        {
            "Movie": "The Replacements",
            "Review": "Pretty funny at times",
            "Rating": 62
        },
        {
            "Movie": "The Replacements",
            "Review": "Silly, but fun",
            "Rating": 65
        },
        {
            "Movie": "The Da Vinci Code",
            "Review": "Fun, but a little far fetched",
            "Rating": 65
        },
        {
            "Movie": "The Replacements",
            "Review": "Pretty funny at times",
            "Rating": 62
        },
        {
            "Movie": "The Replacements",
            "Review": "Silly, but fun",
            "Rating": 65
        },
        {
            "Movie": "The Da Vinci Code",
            "Review": "Fun, but a little far fetched",
            "Rating": 65
        }
    ]
```

### Exercise 4.10: Retrieve all people who have produced a movie, but have not directed a movie (Solution)

```
    MATCH (a:Person)-[:PRODUCED]->(m:Movie)
    WHERE NOT ((a)-[:DIRECTED]->(:Movie))
    RETURN a.name, m.title

    [
        {
            "Name": "Joel Silver",
            "Movie": "The Matrix"
        },
        {
            "Name": "Joel Silver",
            "Movie": "The Matrix Reloaded"
        },
        {
            "Name": "Joel Silver",
            "Movie": "The Matrix Revolutions"
        },
        {
            "Name": "Nora Ephron",
            "Movie": "When Harry Met Sally"
        },
        {
            "Name": "Stefan Arndt",
            "Movie": "Cloud Atlas"
        },
        {
            "Name": "Lilly Wachowski",
            "Movie": "V for Vendetta"
        },
        {
            "Name": "Lana Wachowski",
            "Movie": "V for Vendetta"
        },
        {
            "Name": "Joel Silver",
            "Movie": "V for Vendetta"
        }
    ]
```

### Exercise 4.11: Retrieve the movies and their actors where one of the actors also directed the movie (Solution)

```
    MATCH (a1:Person)-[:ACTED_IN]->(m:Movie)<-[:ACTED_IN]-(a2:Person)
    WHERE exists( (a2)-[:DIRECTED]->(m) )
    RETURN  a1.name as Actor, a2.name as `Actor/Director`, m.title as Movie

    [
        {
            "Actor": "Liv Tyler",
            "Actor/Director": "Tom Hanks",
            "Movie": "That Thing You Do"
        },
        {
            "Actor": "Charlize Theron",
            "Actor/Director": "Tom Hanks",
            "Movie": "That Thing You Do"
        },
        {
            "Actor": "Gene Hackman",
            "Actor/Director": "Clint Eastwood",
            "Movie": "Unforgiven"
        },
        {
            "Actor": "Richard Harris",
            "Actor/Director": "Clint Eastwood",
            "Movie": "Unforgiven"
        },
        {
            "Actor": "Jack Nicholson",
            "Actor/Director": "Danny DeVito",
            "Movie": "Hoffa"
        },
        {
            "Actor": "J.T. Walsh",
            "Actor/Director": "Danny DeVito",
            "Movie": "Hoffa"
        },
        {
            "Actor": "John C. Reilly",
            "Actor/Director": "Danny DeVito",
            "Movie": "Hoffa"
        },
        {
            "Actor": "Liv Tyler",
            "Actor/Director": "Tom Hanks",
            "Movie": "That Thing You Do"
        },
        {
            "Actor": "Charlize Theron",
            "Actor/Director": "Tom Hanks",
            "Movie": "That Thing You Do"
        },
        {
            "Actor": "Gene Hackman",
            "Actor/Director": "Clint Eastwood",
            "Movie": "Unforgiven"
        },
        {
            "Actor": "Richard Harris",
            "Actor/Director": "Clint Eastwood",
            "Movie": "Unforgiven"
        },
        {
            "Actor": "John C. Reilly",
            "Actor/Director": "Danny DeVito",
            "Movie": "Hoffa"
        },
        {
            "Actor": "J.T. Walsh",
            "Actor/Director": "Danny DeVito",
            "Movie": "Hoffa"
        },
        {
            "Actor": "Jack Nicholson",
            "Actor/Director": "Danny DeVito",
            "Movie": "Hoffa"
        }
    ]
```

### Exercise 4.12: Retrieve all movies that were released in a set of years (Solution)

```
    MATCH (m:Movie)
    WHERE m.released in [2000, 2004, 2008]
    RETURN m.title, m.released

    [
        {
            "m.title": "Jerry Maguire",
            "m.released": 2000
        },
        {
            "m.title": "The Replacements",
            "m.released": 2000
        },
        {
            "m.title": "Speed Racer",
            "m.released": 2008
        },
        {
            "m.title": "Frost/Nixon",
            "m.released": 2008
        },
        {
            "m.title": "Cast Away",
            "m.released": 2000
        },
        {
            "m.title": "The Polar Express",
            "m.released": 2004
        },
        {
            "m.title": "Jerry Maguire",
            "m.released": 2000
        },
        {
            "m.title": "The Replacements",
            "m.released": 2000
        },
        {
            "m.title": "Speed Racer",
            "m.released": 2008
        },
        {
            "m.title": "Frost/Nixon",
            "m.released": 2008
        },
        {
            "m.title": "Cast Away",
            "m.released": 2000
        },
        {
            "m.title": "The Polar Express",
            "m.released": 2004
        }
    ]
```

### Exercise 4.13: Retrieve the movies that have an actor’s role that is the name of the movie (Solution)

```
    MATCH (a:Person)-[r:ACTED_IN]->(m:Movie)
    WHERE m.title in r.roles
    RETURN  m.title as Movie, a.name as Actor

    [
        {
            "Movie": "Jerry Maguire",
            "Actor": "Tom Cruise"
        },
        {
            "Movie": "Johnny Mnemonic",
            "Actor": "Keanu Reeves"
        },
        {
            "Movie": "Speed Racer",
            "Actor": "Emile Hirsch"
        },
        {
            "Movie": "Hoffa",
            "Actor": "Jack Nicholson"
        },
        {
            "Movie": "Jerry Maguire",
            "Actor": "Tom Cruise"
        },
        {
            "Movie": "Johnny Mnemonic",
            "Actor": "Keanu Reeves"
        },
        {
            "Movie": "Speed Racer",
            "Actor": "Emile Hirsch"
        },
        {
            "Movie": "Hoffa",
            "Actor": "Jack Nicholson"
        }
    ]
```

### Exercise 5.1: Retrieve data using multiple MATCH patterns (Solution)

```
    MATCH (a:Person)-[:ACTED_IN]->(m:Movie)<-[:DIRECTED]-(d:Person),
      (a2:Person)-[:ACTED_IN]->(m)
    WHERE a.name = 'Gene Hackman'
    RETURN m.title as movie, d.name AS director , a2.name AS `co-actors`
```

### Exercise 5.2: Retrieve particular nodes that have a relationship (Solution)

```
    MATCH (p1:Person)-[:FOLLOWS]-(p2:Person)
    WHERE p1.name = 'James Thompson'
    RETURN p1, p2
```

### Exercise 5.3: Modify the query to retrieve nodes that are exactly three hops away (Solution)

```
    MATCH (p1:Person)-[:FOLLOWS*3]-(p2:Person)
    WHERE p1.name = 'James Thompson'
    RETURN p1, p2
```

### Exercise 5.4: Modify the query to retrieve nodes that are one and two hops away (Solution)

```
    MATCH (p1:Person)-[:FOLLOWS*1..2]-(p2:Person)
    WHERE p1.name = 'James Thompson'
    RETURN p1, p2
```

### Exercise 5.5: Modify the query to retrieve particular nodes that are connected no matter how many hops are required (Solution)

```
    MATCH (p1:Person)-[:FOLLOWS*]-(p2:Person)
    WHERE p1.name = 'James Thompson'
    RETURN p1, p2
```

### Exercise 5.6: Specify optional data to be retrieved during the query (Solution)

```
    MATCH (p:Person)
    WHERE p.name STARTS WITH 'Tom'
    OPTIONAL MATCH (p)-[:DIRECTED]->(m:Movie)
    RETURN p.name, m.title
```

### Exercise 5.7: Retrieve nodes by collecting a list (Solution)

```
    MATCH (p:Person)-[:ACTED_IN]->(m:Movie)
    RETURN p.name as actor, collect(m.title) AS `movie list`
```

### Exercise 5.8: Retrieve all movies that Tom Cruise has acted in and the co-actors that acted in the same movie by collecting a list (Solution)

```
    MATCH (p:Person)-[:ACTED_IN]->(m:Movie)<-[:ACTED_IN]-(p2:Person)
    WHERE p.name ='Tom Cruise'
    RETURN m.title as movie, collect(p2.name) AS `co-actors`
```

### Exercise 5.9: Retrieve nodes as lists and return data associated with the corresponding lists (Solution)

```
    MATCH (p:Person)-[:REVIEWED]->(m:Movie)
    RETURN m.title as movie, count(p) as numReviews, collect(p.name) as reviewers
```

### Exercise 5.10: Retrieve nodes and their relationships as list (Solution)

```
    MATCH (d:Person)-[:DIRECTED]->(m:Movie)<-[:ACTED_IN]-(a:Person)
    RETURN d.name AS director, count(a) AS `number actors` , collect(a.name) AS `actors worked with`
```

### Exercise 5.11: Retrieve the actors who have acted in exactly five movies (Solution)

```
    MATCH (a:Person)-[:ACTED_IN]->(m:Movie)
    WITH  a, count(a) AS numMovies, collect(m.title) AS movies
    WHERE numMovies = 5
    RETURN a.name, movies
```

### Exercise 5.12: Retrieve the movies that have at least 2 directors with other optional data (Solution)

```
    MATCH (m:Movie)
    WITH m, size((:Person)-[:DIRECTED]->(m)) AS directors
    WHERE directors >= 2
    OPTIONAL MATCH (p:Person)-[:REVIEWED]->(m)
    RETURN  m.title, p.name
```