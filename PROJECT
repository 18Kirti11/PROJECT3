import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;
import java.util.ArrayList;
import java.util.List;
abstract class Animal {
    private String name;
    private static int createdCount = 0;   

    public Animal(String name) {
        this.name = name;
        createdCount++;
    }

    public String getName() {
        return name;
    }
    public abstract void speak();

    public static int getCreatedCount() {
        return createdCount;
    }
}
class Dog extends Animal {
    public Dog(String name) {
        super(name);
    }
    public void speak() {
        System.out.println(getName() + " says: Woof!");
    }
}

class Cat extends Animal {
    public Cat(String name) {
        super(name);
    }
    public void speak() {
        System.out.println(getName() + " says: Meow!");
    }
}
final class Utils {
    private Utils() {} 

    public static void printSeparator() {
        System.out.println("----------");
    }
}
class AnimalException extends Exception {
    public AnimalException(String msg) {
        super(msg);
    }
}
public class Main {
    public static void main(String[] args) {
        Animal[] zoo = new Animal[2];
        zoo[0] = new Dog("Buddy");
        zoo[1] = new Cat("Whiskers");
        for (Animal a : zoo) {
            a.speak();               
        }

        Utils.printSeparator();
        List<Animal> animalList = new ArrayList<>();
        animalList.add(new Dog("Rex"));
        animalList.add(new Cat("Luna"));
        try {
            feedAnimal(animalList.get(0));
            feedAnimal(null);               
        } catch (AnimalException e) {
            System.err.println("Error: " + e.getMessage());
        } finally {
            System.out.println("Feeding routine finished.");
        }

        Utils.printSeparator();
        System.out.println("Total animals created: " + Animal.getCreatedCount());

        zoo = null;     
        System.gc();         

    }
    private static void feedAnimal(Animal a) throws AnimalException {
        if (a == null) {
            throw new AnimalException("Cannot feed a null animal.");
        }
        System.out.println("Feeding " + a.getName() + "...");
    }

    private static Connection getMySQLConnection() throws SQLException {
        String url = "jdbc:mysql://localhost:3306/testdb";
        String user = "root";
        String password = "password";
        return DriverManager.getConnection(url, user, password);
    }
}
