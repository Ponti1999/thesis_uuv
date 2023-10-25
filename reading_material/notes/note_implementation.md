# Look up

- Ardusub: open-source solution for remotely operated underwater vehicle: [link](https://www.ardusub.com/)

- One of the team (French, phd publication, military) used this tool: [link](https://www.glimpse-alseamar.com/#/login)</br>
  look up the capabilities of this tool and how it can be used for route planning.

- UE5 multi window setup possibility: [link](https://www.unrealengine.com/marketplace/en-US/product/multi-window)


# Water / Fluid Simulation (UE5)

- https://docs.unrealengine.com/5.0/en-US/water-system-in-unreal-engine/
- https://docs.unrealengine.com/5.0/en-US/fluid-simulation-in-unreal-engine/
- https://docs.unrealengine.com/5.0/en-US/fluid-simulation-in-unreal-engine---overview/
- [Video at 1:00:00](https://www.youtube.com/watch?v=k7WLE2kM4po)
- [Water current](https://forums.unrealengine.com/t/water-with-current/150338/3)


# Route planning

database:
- https://data.marine.copernicus.eu/products
- https://data.marine.copernicus.eu/product/GLOBAL_ANALYSISFORECAST_PHY_001_024/description


# Hydrodynamic calculations

- Pricy option ($50+/100+): https://airshaper.com/ and give the result back to the simulator.
- Searching for a framework / other solution for hydrodynamic calculations.
  - https://medium.com/@northamericangeoscientistsorg/hydrodynamic-modeling-with-python-d3ddef0fe2fe
  - (https://journals.sagepub.com/doi/10.1177/1687814017734500)


# Reading material

- Articles:
  - [MDPI](https://www.mdpi.com/search?sort=pubdate&page_count=50&q=Underwater+Vehicle+Simulator&year_from=2018&year_to=2023&featured=&subjects=&journals=&article_types=&countries=)
  - [ScienceDirect](https://www.sciencedirect.com/search?qs=Underwater%20Vehicle%20Simulator&years=2024%2C2018%2C2019%2C2020%2C2021%2C2022%2C2023&lastSelectedFacet=years)
  - [IEEE Xplore](https://ieeexplore.ieee.org/search/searchresult.jsp?queryText=Underwater%20Vehicle%20Simulator&highlight=true&returnFacets=ALL&returnType=SEARCH&matchPubs=true&ranges=2018_2023_Year)



- [Possible public intelligence](https://publicintelligence.net/?s=submarine)
- [Books](https://ftp.idu.ac.id/wp-content/uploads/ebook/tdg/ADNVANCED%20MILITARY%20PLATFORM%20DESIGN/?C=M;O=D)

</br>
</br>

------------------------------------------------------------------------------------------------------

# Communication (UE5 and UUV)

Creating a bidirectional communication system between a physical underwater vehicle (UUV) and a simulator in Unreal Engine 5 (UE5) is a complex task that involves various technologies and protocols. Here are some possibilities for communication between the UE5 simulator and the physical UUV:

MQTT:
MQTT (Message Queuing Telemetry Transport) is a lightweight and efficient publish-subscribe messaging protocol that can be used for communication between the simulator and the UUV. It's a good choice for sending telemetry data and control commands.

TCP/IP or UDP:
You can use standard networking protocols like TCP/IP or UDP for communication. UE5 has built-in networking capabilities that allow you to establish sockets for sending and receiving data between the simulator and the UUV. This approach offers more flexibility in designing your communication protocol.

Serial Communication (USB/RS-232/RS-485):
If your physical UUV supports serial communication via USB, RS-232, or RS-485, you can interface with it directly from your simulator. UE5 can communicate with serial devices using plugins or custom code. This is a common method for connecting to hardware devices.

WebSocket:
WebSocket is a communication protocol that provides full-duplex communication channels over a single TCP connection. You can use WebSocket libraries or plugins to enable communication between the simulator and the UUV. It's suitable for real-time data exchange.

RESTful API:
Implement a RESTful API on the UUV's side and use HTTP requests from UE5 to send commands and receive data. This approach is straightforward and works well for web-based applications or when a more standardized interface is desired.

Custom Middleware:
If you have specific requirements or constraints, you can develop custom middleware or communication protocols tailored to your project's needs. This might involve creating custom UE5 plugins or standalone software for the UUV.

ROS (Robot Operating System):
If your UUV uses ROS for control and communication, you can integrate ROS with UE5. ROS provides a framework for building robotic systems and includes support for various communication methods.

MQTTROS:
If you're using ROS on your UUV, you can combine MQTT and ROS by using the MQTTROS bridge. This allows you to publish and subscribe to ROS topics via MQTT, potentially simplifying the integration with UE5.

Simulink:
If you're using MathWorks Simulink for UUV control, consider using Simulink's built-in capabilities for simulation and communication. You can then interface Simulink with UE5 through suitable methods.

When choosing a communication method, consider factors such as latency, bandwidth, reliability, and ease of implementation. The choice will depend on your project's specific requirements and the capabilities of your physical UUV. Additionally, be mindful of security and data validation when implementing bidirectional communication between the simulator and the UUV to ensure safe and reliable operation.

As of my last knowledge update in September 2021, UE5 did not have native support for MQTTROS, and integration would require custom development.


</br>


# PID Controller

### [LINK](https://gamedevtricks.com/post/pid-controllers/)


As of my last knowledge update in September 2021, Unreal Engine 5 (UE5) doesn't have built-in support for PID controllers out of the box. However, you can create a PID controller in UE5 by writing custom Blueprints or code using C++.

Here are the general steps to create a PID controller in UE5:

Create a Blueprint Class:
Start by creating a Blueprint Class, which will represent your PID controller. This Blueprint will contain the logic for the PID controller.

Define Variables:
Inside your PID controller Blueprint, define variables for the PID constants (Kp, Ki, Kd) and any other necessary variables like target setpoint, current value, and error terms.

Implement the PID Algorithm:
In your Blueprint, implement the PID algorithm using UE5's scripting capabilities. The PID algorithm consists of three main components:

Proportional (P): Calculate the proportional term by multiplying the error (difference between the setpoint and current value) by the proportional constant (Kp).

Integral (I): Calculate the integral term by summing up the error over time and multiplying it by the integral constant (Ki).

Derivative (D): Calculate the derivative term by finding the rate of change of the error and multiplying it by the derivative constant (Kd).

Combine these three terms to calculate the controller output.

Apply Control Output:
Use the calculated controller output to control your system. This might involve adjusting the position, velocity, or any other parameter of the system you are controlling.

Tune the PID Constants:
PID controllers require tuning to achieve desired performance. You'll need to experiment with different values of Kp, Ki, and Kd to achieve the desired control behavior.

Testing and Debugging:
Test your PID controller in a simulation environment to ensure that it behaves as expected. Monitor the controller's performance and make adjustments as needed.

If you are comfortable with C++ programming, you can also create a custom C++ class for the PID controller. Here's a simplified example of how you might create a PID controller in C++ for UE5:

```cpp
#include "YourPIDControllerClass.h"

// Constructor
AYourPIDControllerClass::AYourPIDControllerClass()
{
    // Initialize PID constants
    Kp = 1.0f;
    Ki = 0.0f;
    Kd = 0.0f;
}

// Update function
void AYourPIDControllerClass::Update(float Setpoint, float CurrentValue, float& ControlOutput)
{
    // Calculate error
    float Error = Setpoint - CurrentValue;

    // Calculate P, I, and D terms
    ProportionalTerm = Kp * Error;
    IntegralTerm += Ki * Error;
    DerivativeTerm = Kd * (Error - PreviousError);

    // Calculate the control output
    ControlOutput = ProportionalTerm + IntegralTerm + DerivativeTerm;

    // Update the previous error for the next iteration
    PreviousError = Error;
}
```

This is a simplified example, and you may need to expand upon it to meet your specific requirements.

Keep in mind that PID controllers can be complex to tune and may require fine-tuning for optimal performance in your specific application.
