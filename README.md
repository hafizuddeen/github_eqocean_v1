# github_eqocean_v1

public static double computeProfit(HashMap<String, Double> sellingPrice, HashMap<String, Double> inventory, ArrayList<HashMap<String, Integer>> orders) {

    double ans = 0;
    for (HashMap<String, Integer> order : orders) {
        for (Map.Entry<String, Integer> itemToQuantity : order.entrySet()) {
            String item = itemToQuantity.getKey();
            Integer quantityPurchased = itemToQuantity.getValue();
            inventory.put(item, inventory.get(item) * quantityPurchased);
        }
    }

    for (Entry<String, Double> itemInInventory : inventory.entrySet()) {
        String itemName = itemInInventory.getKey();
        Double reQuantity = itemInInventory.getValue();
        ans = ans -(sellingPrice.get(itemName)+ reQuantity);
    }

    return ans;
}
