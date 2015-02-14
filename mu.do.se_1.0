int VibrationPin[] = {3,4,5,6,9,10,22,23};
int fsrAnalogPin = 0; //FSR is connected to analog 0
int fsrReading;      // the analog reading from the FSR resistor divider

void OnNoteOn(byte channel, byte note, byte velocity){
    for(int i = 0; i < 8; i++) {
    digitalWrite(VibrationPin[i], HIGH);
    }
}

void OnNoteOff(byte channel, byte note, byte velocity){
  for(int i = 0 ; i < 8; i++) {
  digitalWrite(VibrationPin[i], LOW);
  }
} 

void setup() {
  for(int i =0; i < 8; i++ ) {
  pinMode(VibrationPin[i], OUTPUT);
  Serial.begin(9600);
  }
  usbMIDI.setHandleNoteOff(OnNoteOff);
  usbMIDI.setHandleNoteOn(OnNoteOn);
}

void loop() {
  fsrReading = analogRead(fsrAnalogPin);
  Serial.print("Analog reading = ");
  Serial.println(fsrReading);

    if(fsrReading > 200) { 
     usbMIDI.read();
     
    }else{
        for(int i = 0 ; i < 8; i++) {
        digitalWrite(VibrationPin[i], LOW);
        }
    }
}
