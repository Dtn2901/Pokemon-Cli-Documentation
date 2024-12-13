
The **Pokémon CLI App** is a command-line tool designed to interact with the **PokéAPI** and provide users with information about Pokémon, their types, and type effectiveness in battles. The app allows users to query Pokémon data, check their type(s), and evaluate how one type performs against another in terms of attack/defense effectiveness. The application is built using Python and follows a modular structure for scalability and easy maintenance.

## Features of the Application

- **Fetch Pokémon Data**: Retrieve a Pokémon's type(s) from the PokéAPI.
- **Type Effectiveness**: Check how effective a Pokémon's type is against other types for both attack and defense.
- **Error Handling**: Proper error messages for invalid inputs or API failures.
- **Modular Architecture**: Separated classes for Pokémon, types, and effectiveness calculations.

## Installation Steps and Requirements

### Prerequisites
- **Python 3.8 or higher** is required.
- **`requests` library** for handling API requests.

### Installation Steps

1. **Clone the Repository**
   First, clone the repository from GitHub to your local machine:
   ```bash
   git clone https://github.com/Dtn2901/Pokemon-App.git
   cd Pokemon-App
   ```

2. **Set Up a Virtual Environment**
   Create and activate a virtual environment to manage dependencies:
   ```bash
   # Create the virtual environment
   python -m venv env

   # Activate the environment (Windows)
   .\env\Scripts\activate

   # Activate the environment (macOS/Linux)
   source env/bin/activate
   ```

3. **Install Dependencies**
   Install the required dependencies listed in the `requirements.txt`:
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Application**
   After the environment is set up, run the main script:
   ```bash
   python main.py
   ```

## How to Use

- **Fetch Pokémon Information**: To get data about a specific Pokémon, type the Pokémon's name. For example:
  ```bash
  Pikachu
  ```

- **Check Type Effectiveness**: To check the effectiveness of one type against another, type the Pokémon's name followed by the attacking type:
  ```bash
  Charmander water
  ```

- **Exit the Application**: Type `exit` to exit the application.

## Directory Structure

```plaintext
pokemon_cli_app/
├── env/                     # Virtual environment directory
├── effectiveness.py          # Class for type effectiveness calculations
├── main.py                   # Main application script
├── pokemon.py                # Class for handling Pokémon attributes
├── requirements.txt          # Dependency file
└── type.py                   # Class for handling type details
```

## Code Documentation

### **pokemon.py**

**Purpose**: The `pokemon.py` file defines the `Pokemon` class, which is responsible for retrieving and managing the type(s) of a Pokémon.

```python
class Pokemon:
    """
    Represents a Pokémon and its type(s).
    """
    def __init__(self, name):
        """
        Initializes a Pokémon object with a name and fetches its types from the PokéAPI.
        Args:
        - name (str): The name of the Pokémon.
        """
        self.name = name
        self.types = self.get_types()

    def get_types(self):
        """
        Fetches the types of the Pokémon from the PokéAPI.
        Returns:
        - list: A list of types associated with the Pokémon (e.g., ['fire', 'electric']).
        """
        # API call to fetch Pokémon types
        pass
```

**Methods/Functions**:
- **`__init__(self, name)`**: Initializes the object with a Pokémon's name and retrieves its types.
  - **Parameters**: `name (str)` — the name of the Pokémon.
  - **Returns**: None, but it calls the `get_types()` method to populate `self.types`.
  
- **`get_types(self)`**: Makes an API request to fetch the types of the Pokémon from the PokéAPI.
  - **Parameters**: None
  - **Returns**: A list of Pokémon types.

### **type.py**

**Purpose**: The `type.py` file defines the `Type` class, which manages the properties and effectiveness of Pokémon types.

```python
class Type:
    """
    Represents a Pokémon type and its effectiveness against other types.
    """
    def __init__(self, name):
        """
        Initializes the Type object.
        Args:
        - name (str): The name of the Pokémon type (e.g., 'fire', 'water').
        """
        self.name = name
        self.effectiveness = self.get_effectiveness()

    def get_effectiveness(self):
        """
        Fetches the effectiveness of the type against other types from the PokéAPI.
        Returns:
        - dict: A dictionary containing effectiveness data for the type.
        """
        # API call to fetch effectiveness data
        pass
```

**Methods/Functions**:
- **`__init__(self, name)`**: Initializes the object with the name of the Pokémon type.
  - **Parameters**: `name (str)` — the name of the type (e.g., 'fire', 'water').
  - **Returns**: None, but it calls `get_effectiveness()` to populate `self.effectiveness`.

- **`get_effectiveness(self)`**: Fetches the effectiveness of the Pokémon type against others.
  - **Parameters**: None
  - **Returns**: A dictionary with effectiveness information for the type.

### **effectiveness.py**

**Purpose**: The `effectiveness.py` file defines the `Effectiveness` class, which is responsible for calculating how effective one type is against another in battle.

```python
class Effectiveness:
    """
    Handles type effectiveness calculations between Pokémon types.
    """
    def __init__(self, attack_type, defense_type):
        """
        Initializes the Effectiveness object to calculate type interactions.
        Args:
        - attack_type (str): The attacking type.
        - defense_type (str): The defending type.
        """
        self.attack_type = attack_type
        self.defense_type = defense_type

    def calculate_effectiveness(self):
        """
        Determines the effectiveness of the attacking type against the defending type.
        Returns:
        - str: A message indicating the effectiveness (e.g., "super effective").
        """
        # Logic to calculate effectiveness
        pass
```

**Methods/Functions**:
- **`__init__(self, attack_type, defense_type)`**: Initializes the object with the attacking and defending types.
  - **Parameters**: `attack_type (str)` — the attacking Pokémon's type, `defense_type (str)` — the defending Pokémon's type.
  - **Returns**: None.

- **`calculate_effectiveness(self)`**: Calculates the effectiveness of one type against another.
  - **Parameters**: None
  - **Returns**: A string indicating the effectiveness, such as "super effective", "not very effective", etc.

### Imported Libraries

- **`requests`**: The `requests` library is used to make HTTP requests to the PokéAPI and retrieve data. It is licensed under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).

### Purpose and Source of Imported Code

- **PokéAPI**: All Pokémon and type-related data is fetched using the **PokéAPI** (https://pokeapi.co/). This API is free to use under its terms of service and provides rich, structured data for all Pokémon and their attributes.
- **requests**: Used for making HTTP requests to the PokéAPI.

## Error Handling and Best Practices

- **Invalid Pokémon or Type Name**: If a user enters an invalid name or type, the app provides a clear and friendly error message, guiding the user to re-enter a valid name.
- **API Connection Failures**: If there is an issue connecting to the PokéAPI (e.g., network problems), the app will display a message informing the user to check their connection.
- **Modular Structure**: Each class has a single responsibility (e.g., `Pokemon` handles Pokémon data, `Type` handles type data), ensuring the app is maintainable and scalable.


This documentation ensures the project is well-understood and easily maintained.

