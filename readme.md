"""
RC Circuit Simulator
---------------------
This program simulates charging and discharging of a capacitor
in an RC circuit using mathematical models.

Equations:
Charging:    Vc(t) = V * (1 - e^(-t/RC))
Discharging: Vc(t) = V * e^(-t/RC)

Author: Student
"""

import numpy as np
import matplotlib.pyplot as plt


# ===============================
# Function Definitions
# ===============================

def charging_voltage(V, R, C, t):
    """Calculate capacitor charging voltage"""
    return V * (1 - np.exp(-t / (R * C)))


def discharging_voltage(V, R, C, t):
    """Calculate capacitor discharging voltage"""
    return V * np.exp(-t / (R * C))


def time_constant(R, C):
    """Calculate RC time constant"""
    return R * C


# ===============================
# Main Program
# ===============================

def main():

    print("RC Circuit Simulator")
    print("--------------------")

    # User Input
    R = float(input("Enter Resistance (Ohms): "))
    C = float(input("Enter Capacitance (Farads): "))
    V = float(input("Enter Supply Voltage (Volts): "))

    # Time range
    t = np.linspace(0, 0.01, 1000)

    # Calculations
    charge_curve = charging_voltage(V, R, C, t)
    discharge_curve = discharging_voltage(V, R, C, t)

    tau = time_constant(R, C)

    # Display Time Constant
    print("\nTime Constant (τ = RC):", tau, "seconds")

    # Plot Results
    plt.figure(figsize=(8, 5))

    plt.plot(t, charge_curve, label="Charging Curve")
    plt.plot(t, discharge_curve, label="Discharging Curve")

    plt.xlabel("Time (seconds)")
    plt.ylabel("Voltage (Volts)")
    plt.title("RC Circuit Charging and Discharging Simulation")
    plt.legend()
    plt.grid(True)

    plt.show()


# ===============================
# Program Entry Point
# ===============================

if __name__ == "__main__":
    main()