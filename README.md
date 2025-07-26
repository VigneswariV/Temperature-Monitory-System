# Temperature-Monitory-System
const int buttonPin = 2;   // Push button connected to D2
int counter = 0;
int buttonState = 0;
int lastButtonState = 0;

void setup() {
  pinMode(buttonPin, INPUT);
  Serial.begin(9600);      // Start Serial Monitor
}

void loop() {
  buttonState = digitalRead(buttonPin);

  // Rising edge detection (button press)
  if (buttonState == HIGH && lastButtonState == LOW) {
    counter++;
    Serial.print("Button Pressed: ");
    Serial.println(counter);
    delay(200); // Debounce delay
  }

  lastButtonState = buttonState;
}
