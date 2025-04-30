// Task 1: Change the name of "Riverside Park" to "Riverside Greenspace"
parks.forEach(park => {
  if (park.name === "Riverside Park") {
    park.name = "Riverside Greenspace";
  }
});

// Task 2: Change the name of the tree species "Maple" to "Sugar Maple" in "Central Park"
parks.forEach(park => {
  if (park.name === "Central Park") {
    park.trees.forEach(tree => {
      if (tree.species === "Maple") {
        tree.species = "Sugar Maple";
      }
    });
  }
});

// Task 3: Add a new tree to "Central Park"
parks.forEach(park => {
  if (park.name === "Central Park") {
    park.trees.push({
      species: "Birch",
      age: 7,
      health: "Good",
      height: 18
    });
  }
});

// Task 4: Retrieve a list of all tree species in "Central Park"
const centralParkTrees = parks
  .find(park => park.name === "Central Park")
  .trees.map(tree => tree.species);

// Task 5: Calculate the average age of all trees
const totalAge = parks
  .flatMap(park => park.trees)
  .reduce((sum, tree) => sum + tree.age, 0);
const totalTrees = parks.flatMap(park => park.trees).length;
const averageTreeAge = totalAge / totalTrees;

// Task 6: Determine the tallest tree
const tallestTree = parks
  .flatMap(park => park.trees)
  .reduce((tallest, tree) => (tree.height > tallest.height ? tree : tallest), { height: 0 });

// Task 7: Remove the "playground" facility from "Central Park"
parks.forEach(park => {
  if (park.name === "Central Park") {
    park.facilities = park.facilities.filter(facility => facility !== "playground");
  }
});

// Task 8: Convert the parks array into a JSON object
const parksJSON = JSON.stringify(parks, null, 2);

// Task 9: Display the name and facilities of the first park
console.log(`Name: ${parks[0].name}`);
console.log(`Facilities: ${parks[0].facilities.join(', ')}`);

// Task 10: Display the species of the third park
const thirdParkSpecies = parks[2].trees.map(tree => tree.species);
console.log(`Species in third park: ${thirdParkSpecies.join(', ')}`);
