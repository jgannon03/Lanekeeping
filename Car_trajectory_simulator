from scipy.integrate import solve_ivp
import numpy as np
import matplotlib.pyplot as plt


class Car:
    def __init__(self, length=2.3, velocity=5, x=0, y=0, theta=0): ##user provided
        self.length = length
        self.velocity = velocity
        self.x = x
        self.y = y
        self.theta = theta


    def move(self, steering_angle, dt): ##simulate the trajectory for time =0, to time t = 0+dt starting from z_initial
        z_initial = [self.x, self.y, self.theta]

        def system_dynamics(t, z):
            theta = z[2]
            return [self.velocity * np.cos(theta),
                    self.velocity * np.sin(theta),
                    self.velocity * np.tan(steering_angle) / self.length]

        z_initial = [self.x, self.y, self.theta]
        solution = solve_ivp(system_dynamics,
                             [0, dt], ##0+dt = dt
                             z_initial)
        self.x = solution.y[0][-1]
        self.y = solution.y[1][-1]
        self.theta = solution.y[2][-1]

abarth = Car()
abarth.move(0.01, 0.005)
#where is the abarth
print(abarth.x)
