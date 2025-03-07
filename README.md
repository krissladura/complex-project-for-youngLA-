# complex-project-for-youngLA-



class GymInventoryManager:
    def __init__(self):
        self.gym_clothing = {"Over sized": [], "Compression": [], "Super sized": []}
        self.supplements = {"Creatine": [], "Protein": [], "Pre-Workout": []}
        self.accessories = {"Shakers": [], "Bracelets": [], "Notebooks": []}

    class YoungLA_Gym_clothing:
        def __init__(self):
            self.gym_clothing = {"Over sized": [], "Compression": [], "Super sized": []}

        def add_gym_clothing(self, category, name, price, stock):
            if category in self.gym_clothing:
                self.gym_clothing[category].append({"name": name, "price": price, "stock": stock})
            else:
                print("Invalid category!")

        def display_gym_clothing(self):
            print("\nGym Clothing Inventory:")
            for category, items in self.gym_clothing.items():
                print(f"{category}:")
                for item in items:
                    print(f"  - {item['name']} (Price: ${item['price']}, Stock: {item['stock']})")

        def search_gym_clothing(self, name):
            for category, items in self.gym_clothing.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        return item
            return "Item not found"

        def update_gym_clothing(self, name, new_price, new_stock):
            for category, items in self.gym_clothing.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        item['price'] = new_price
                        item['stock'] = new_stock
                        return "Updated successfully"
            return "Item not found"

        def remove_gym_clothing(self, name):
            for category, items in self.gym_clothing.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        items.remove(item)
                        return "Removed successfully"
            return "Item not found"

    class Supplements_manager:
        def __init__(self):
            self.supplements = {"Creatine": [], "Protein": [], "Pre-Workout": []}

        def add_supplement(self, category, name, flavor, price, stock):
            if category in self.supplements:
                self.supplements[category].append({"name": name, "flavor": flavor, "price": price, "stock": stock})
            else:
                print("Invalid category!")

        def display_supplements(self):
            print("\nSupplement Inventory:")
            for category, items in self.supplements.items():
                print(f"{category}:")
                for item in items:
                    print(f"  - {item['name']} ({item['flavor']} flavor) (Price: ${item['price']}, Stock: {item['stock']})")

        def search_supplement(self, name):
            for category, items in self.supplements.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        return item
            return "Item not found"

        def update_supplement(self, name, new_price, new_stock):
            for category, items in self.supplements.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        item['price'] = new_price
                        item['stock'] = new_stock
                        return "Updated successfully"
            return "Item not found"

        def remove_supplement(self, name):
            for category, items in self.supplements.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        items.remove(item)
                        return "Removed successfully"
            return "Item not found"


    class Acessory_manager:
        def __init__(self):
            self.accessories = {"Shakers": [], "Bracelets": [], "Notebooks": []}

        def add_accessory(self, category, name, price, stock):
            if category in self.accessories:
                self.accessories[category].append({"name": name, "price": price, "stock": stock})
            else:
                print("Invalid category!")

        def display_accessories(self):
            print("\nAccessories Inventory:")
            for category, items in self.accessories.items():
                print(f"{category}:")
                for item in items:
                    print(f"  - {item['name']} (Price: ${item['price']}, Stock: {item['stock']})")

        def search_accessory(self, name):
            for category, items in self.accessories.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        return item
            return "Item not found"

        def update_accessory(self, name, new_price, new_stock):
            for category, items in self.accessories.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        item['price'] = new_price
                        item['stock'] = new_stock
                        return "Updated successfully"
            return "Item not found"

        def remove_accessory(self, name):
            for category, items in self.accessories.items():
                for item in items:
                    if item['name'].lower() == name.lower():
                        items.remove(item)
                        return "Removed successfully"
            return "Item not found"


# New OutfitRecommender Class
class AI_Outfit_Recommender:
    def __init__(self, gym_inventory):
        self.gym_inventory = gym_inventory

    def recommend_outfit(self, category_preference):
        recommended_outfits = []

        # Checking gym clothing inventory based on category preference
        if category_preference in self.gym_inventory.gym_clothing:
            clothing_items = self.gym_inventory.gym_clothing[category_preference]
            for item in clothing_items:
                if item['stock'] > 0:  # Recommend if stock is available
                    recommended_outfits.append(f"Gym Clothing: {item['name']} - ${item['price']}")

        # Checking accessories inventory
        for category, items in self.gym_inventory.accessories.items():
            for item in items:
                if item['stock'] > 0:  # Recommend if stock is available
                    recommended_outfits.append(f"Accessory: {item['name']} - ${item['price']}")

        # Return recommendations
        if recommended_outfits:
            return "\n".join(recommended_outfits)
        else:
            return "No items available for your preference!"

    def recommend_supplements(self):
        recommended_supplements = []

        # Checking supplements inventory
        for category, items in self.gym_inventory.supplements.items():
            for item in items:
                if item['stock'] > 0:  # Recommend if stock is available
                    recommended_supplements.append(f"Supplement: {item['name']} ({item['flavor']} flavor) - ${item['price']}")

        # Return recommendations
        if recommended_supplements:
            return "\n".join(recommended_supplements)
        else:
            return "No supplements available!"



# Initialize the GymInventoryManager
#
gym_inventory = GymInventoryManager()

# Initialize the individual managers
gym_clothing_manager = gym_inventory.YoungLA_Gym_clothing()
supplements_manager = gym_inventory.Supplements_manager()
accessory_manager = gym_inventory.Acessory_manager()

# Adding Gym Clothing Items
gym_clothing_manager.add_gym_clothing("Over sized", "YoungLA Pump Cover", 45, 10)
gym_clothing_manager.add_gym_clothing("Compression", "YoungLA Compression Tee", 35, 5)
gym_clothing_manager.add_gym_clothing("Super sized", "YoungLA Super Oversized Tee", 50, 7)

# Adding Supplements
supplements_manager.add_supplement("Creatine", "YoungLA Monohydrate", "Unflavored", 30, 20)
supplements_manager.add_supplement("Protein", "YoungLA Whey Protein", "Chocolate", 55, 15)
supplements_manager.add_supplement("Pre-Workout", "YoungLA Pre Elite", "Blue Razz", 40, 12)

# Adding Accessories
accessory_manager.add_accessory("Shakers", "YoungLA Shaker Bottle", 15, 25)
accessory_manager.add_accessory("Bracelets", "YoungLA Gym Bracelet", 10, 30)
accessory_manager.add_accessory("Notebooks", "YoungLA Gym Journal", 20, 12)

# Display all inventories
gym_clothing_manager.display_gym_clothing()
supplements_manager.display_supplements()
accessory_manager.display_accessories()

# Searching for an item
print("\nSearching for 'YoungLA Pump Cover'...")
print(gym_clothing_manager.search_gym_clothing("YoungLA Pump Cover"))

# Updating an item's price and stock
print("\nUpdating 'YoungLA Compression Tee'...")
print(gym_clothing_manager.update_gym_clothing("YoungLA Compression Tee", 38, 8))

# Display updated inventory
gym_clothing_manager.display_gym_clothing()

# AI Outfit Recommender Usage
outfit_recommender = AI_Outfit_Recommender(gym_inventory)

# Recommend outfit based on preference
print("\nOutfit Recommendation for 'Over sized' Fit:")
print(outfit_recommender.recommend_outfit("Over sized"))

# Recommend supplements
print("\nSupplement Recommendations:")
print(outfit_recommender.recommend_supplements())


def test_gym_inventory():
    # Initialize managers
    gym_inventory = GymInventoryManager()
    clothing_manager = GymInventoryManager.YoungLA_Gym_clothing()
    supplement_manager = GymInventoryManager.Supplements_manager()
    accessory_manager = GymInventoryManager.Acessory_manager()
    outfit_recommender = AI_Outfit_Recommender(gym_inventory)

    print("\n===== ADDING ITEMS =====")
    # Add Gym Clothing
    clothing_manager.add_gym_clothing("Over sized", "Legacy Oversized Tee", 35, 10)
    clothing_manager.add_gym_clothing("Compression", "Tight Fit Long Sleeve", 40, 15)

    # Add Supplements
    supplement_manager.add_supplement("Creatine", "Pure Creatine Monohydrate", "Unflavored", 25, 20)
    supplement_manager.add_supplement("Pre-Workout", "High Stim Pre", "Blue Raspberry", 45, 12)

    # Add Accessories
    accessory_manager.add_accessory("Shakers", "YoungLA Shaker Bottle", 15, 50)
    accessory_manager.add_accessory("Bracelets", "Motivation Wristband", 10, 30)

    print("\n===== DISPLAY INVENTORY =====")
    clothing_manager.display_gym_clothing()
    supplement_manager.display_supplements()
    accessory_manager.display_accessories()

    print("\n===== SEARCH ITEMS =====")
    print(clothing_manager.search_gym_clothing("Legacy Oversized Tee"))
    print(supplement_manager.search_supplement("High Stim Pre"))
    print(accessory_manager.search_accessory("YoungLA Shaker Bottle"))

    print("\n===== UPDATE ITEMS =====")
    print(clothing_manager.update_gym_clothing("Legacy Oversized Tee", 30, 8))
    print(supplement_manager.update_supplement("High Stim Pre", 42, 10))
    print(accessory_manager.update_accessory("YoungLA Shaker Bottle", 13, 45))

    print("\n===== REMOVE ITEMS =====")
    print(clothing_manager.remove_gym_clothing("Tight Fit Long Sleeve"))
    print(supplement_manager.remove_supplement("Pure Creatine Monohydrate"))
    print(accessory_manager.remove_accessory("Motivation Wristband"))

    print("\n===== DISPLAY AFTER UPDATES =====")
    clothing_manager.display_gym_clothing()
    supplement_manager.display_supplements()
    accessory_manager.display_accessories()

    print("\n===== OUTFIT & SUPPLEMENT RECOMMENDATIONS =====")
    print(outfit_recommender.recommend_outfit("Over sized"))
    print(outfit_recommender.recommend_supplements())


# Run test
test_gym_inventory()

