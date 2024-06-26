# SDA
#PUSH PROJECT CODESPACE

import random
import time
import matplotlib.pyplot as plt

class SecurityCamera:
    def __init__(self):
        self.status = 'Off'

    def turn_on(self):
        self.status = 'On'
        print("Security Camera is ON")

    def turn_off(self):
        self.status = 'Off'
        print("Security Camera is OFF")

    def get_status(self):
        return self.status

class MotionSensor:
    def __init__(self):
        self.detected_motion = False

    def detect_motion(self):
        # Simulate motion detection
        self.detected_motion = random.choice([True, False])
        return self.detected_motion

class Thermostat:
    def __init__(self):
        self.current_temperature = 22  # Initial temperature in Celsius

    def adjust_temperature(self, desired_temperature):
        # Simulate adjusting temperature
        if self.current_temperature < desired_temperature:
            self.current_temperature += 1
        elif self.current_temperature > desired_temperature:
            self.current_temperature -= 1

    def get_current_temperature(self):
        return self.current_temperature

class SmartLighting:
    def __init__(self):
        self.light_status = 'Off'

    def turn_on(self):
        self.light_status = 'On'
        print("Smart Lighting is ON")

    def turn_off(self):
        self.light_status = 'Off'
        print("Smart Lighting is OFF")

    def get_status(self):
        return self.light_status

class VoiceAssistant:
    def __init__(self):
        self.activated = False

    def activate(self):
        self.activated = True
        print("Voice Assistant Activated")

    def deactivate(self):
        self.activated = False
        print("Voice Assistant Deactivated")

    def get_status(self):
        return self.activated
class SmartHomeSimulation:
    def __init__(self):
        self.camera = SecurityCamera()
        self.motion_sensor = MotionSensor()
        self.thermostat = Thermostat()
        self.lighting = SmartLighting()
        self.voice_assistant = VoiceAssistant()

    def simulate(self, cycles=20):
        for _ in range(cycles):
            # Simulate random events triggering actions
            if random.random() < 0.3:
                if self.motion_sensor.detect_motion():
                    self.camera.turn_on()
                    print("Motion Detected!")
                else:
                    print("No Motion Detected")

            if random.random() < 0.5:
                desired_temp = random.randint(18, 25)
                self.thermostat.adjust_temperature(desired_temp)
                print(f"Current Temperature: {self.thermostat.get_current_temperature()}°C")

            if random.random() < 0.4:
                self.lighting.turn_on()
                print("Smart Lighting is ON")

            if random.random() < 0.2:
                self.voice_assistant.activate()
                print("Voice Assistant Activated")

            # Visualize the state of devices
            self.plot_device_states()
            time.sleep(1)

    def plot_device_states(self):
        plt.clf()
        devices = ['Security Camera', 'Smart Lighting', 'Voice Assistant']
        statuses = [self.camera.get_status() == 'On', self.lighting.get_status() == 'On', self.voice_assistant.get_status()]
        colors = ['red', 'green', 'blue']
        plt.bar(devices, statuses, color=colors)
        plt.ylim(0, 1.5)
        plt.ylabel('Status')
        plt.title('Smart Home Device Status')
        plt.pause(0.1)

if __name__ == "__main__":
    plt.ion()  # Turn on interactive mode for real-time plotting

    simulation = SmartHomeSimulation()
    simulation.simulate()

    plt.ioff()  # Turn off interactive mode
    plt.show()  # Display the final plot

