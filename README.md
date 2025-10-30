#  function Vehicle(type) {
  this.type = type;
}

Vehicle.prototype.describe = function() {
  return `This is a ${this.type}`;
};

function Car(brand) {
  Vehicle.call(this, 'car');
  this.brand = brand;
}

Car.prototype = Object.create(Vehicle.prototype);
Car.prototype.constructor = Car;

Car.prototype.describe = function() {
  return Vehicle.prototype.describe.call(this) + ` made by ${this.brand}`;
};

const tesla = new Car('Tesla');
console.log(tesla.describe());
console.log(tesla.constructor.name);
