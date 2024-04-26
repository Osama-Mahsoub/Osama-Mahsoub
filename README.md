#include <stdio.h>
#include <string.h>

// Structure to represent a car
struct Car {
    int id;
    char brand[50];
    char model[50];
    int year;
    float price;
    int available;
};

// Function to display available cars
void displayAvailableCars(struct Car cars[], int size) {
    printf("Available Cars:\n");
    for (int i = 0; i < size; i++) {
        if (cars[i].available) {
            printf("Car ID: %d, Brand: %s, Model: %s, Year: %d, Price: %.2f\n", cars[i].id, cars[i].brand, cars[i].model, cars[i].year, cars[i].price);
        }
    }
}

// Function to rent a car
void rentCar(struct Car cars[], int size, int carId) {
    for (int i = 0; i < size; i++) {
        if (cars[i].id == carId && cars[i].available) {
            cars[i].available = 0;
            printf("Car ID %d has been rented.\n", carId);
            return;
        }
    }
    printf("Car ID %d is not available for rent.\n", carId);
}

int main() {
    // Sample data for cars
    struct Car cars[3] = {
        {1, "Toyota", "Camry", 2020, 50.0, 1},
        {2, "Honda", "Civic", 2019, 45.0, 1},
        {3, "Ford", "Fusion", 2018, 55.0, 0}
    };

    displayAvailableCars(cars, 3);

    rentCar(cars, 3, 2);

    displayAvailableCars(cars, 3);

    return 0;
}
