#include <iostream>
#include <vector>
#include <string>

class Artifact {
public:
    std::string name;
    std::string description;

    Artifact(std::string n, std::string d) : name(n), description(d) {}

    void display() {
        std::cout << "Artifact: " << name << "\nDescription: " << description << std::endl;
    }
};

class Character {
public:
    std::string name;
    std::string role;
    int power;

    Character(std::string n, std::string r, int p) : name(n), role(r), power(p) {}

    void display() {
        std::cout << "Character: " << name << "\nRole: " << role << "\nPower: " << power << std::endl;
    }
};

class Location {
public:
    std::string name;
    std::string description;

    Location(std::string n, std::string d) : name(n), description(d) {}

    void display() {
        std::cout << "Location: " << name << "\nDescription: " << description << std::endl;
    }
};

class Event {
public:
    std::string description;
    std::vector<Character> charactersInvolved;
    std::vector<Artifact> artifactsInvolved;
    Location location;

    Event(std::string d, std::vector<Character> c, std::vector<Artifact> a, Location l)
        : description(d), charactersInvolved(c), artifactsInvolved(a), location(l) {}

    void display() {
        std::cout << "Event: " << description << "\nLocation: " << location.name << "\n";
        std::cout << "Characters Involved:\n";
        for (auto& character : charactersInvolved) {
            character.display();
            std::cout << "\n";
        }
        std::cout << "Artifacts Involved:\n";
        for (auto& artifact : artifactsInvolved) {
            artifact.display();
            std::cout << "\n";
        }
    }
};

int main() {
    Character hero("Arthur", "Knight", 100);
    Character villain("Morgana", "Sorceress", 120);

    Artifact sword("Excalibur", "The legendary sword of King Arthur.");
    Artifact staff("Morgana's Staff", "A powerful magical staff.");

    Location camelot("Camelot", "The legendary castle and court of King Arthur.");

    std::vector<Character> characters = {hero, villain};
    std::vector<Artifact> artifacts = {sword, staff};

    Event battle("The final battle between Arthur and Morgana.", characters, artifacts, camelot);

    battle.display();

    return 0;
}
