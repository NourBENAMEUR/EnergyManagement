import java.util.ArrayList;
import java.util.List;

abstract class Component {
    public abstract String getDetails();
}

class Battery extends Component {
    private int capacity;

    public Battery(int capacity) {
        this.capacity = capacity;
    }

    public String getDetails() {
        return "Battery - Capacity: " + capacity + " kWh";
    }

    public int getCapacity() {
        return capacity;
    }
}

class SolarPanel extends Component {
    private int power;

    public SolarPanel(int power) {
        this.power = power;
    }

    public String getDetails() {
        return "Solar Panel - Power: " + power + " kW";
    }

    public int generatePower() {
        return power;
    }
}

class EnergyManager {
    private List<Component> components;

    public EnergyManager() {
        this.components = new ArrayList<>();
    }

    public void addComponent(Component component) {
        components.add(component);
    }

    public void removeComponent(Component component) {
        components.remove(component);
    }

    public int calculateTotalCapacity() {
        int totalCapacity = 0;
        for (Component component : components) {
            if (component instanceof Battery) {
                totalCapacity += ((Battery) component).getCapacity();
            }
        }
        return totalCapacity;
    }
}
