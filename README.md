## Demo
![roller-coaster-sim](https://github.com/amin1nasim/Roller-Coaster-Simulation/assets/49731000/b8834a54-fb09-4e21-84ed-e3ec397a7cf9)

## Mathematical Concepts of This Simulation

### Hermite Curve
Starting with a set of control points, I utilized Cubic Hermite Splines to connect them and create a smooth curve (track). Unlike linear interpolation, Hermite Spline allows for the creation of smooth curves by specifying tangents at each control point.

Given to consecutive control points where their positions are $p_0$ and  $p_1$, and their tangents $t_0$ and $t_1$, the Hermite Curve is formulated as:

$$ C(t) = m_0(t)p_0 + m_1(t)p_1 + m_2(t)t_0 + m_3(t)t_1 $$

where:

$$ m_0(t) = 2t^3 - 3t^2 + 1  $$

$$ m_1(t) = -2t^3 + 3t^2     $$

$$ m_2(t) = t^3 - 2t^2 + t   $$

$$ m_3(t) = t^3 - t^2        $$


### Catmull-Rom Splines
Catmull-Rom splines were employed to automatically calculate tangents, simplifying the process of creating a smooth curve without manually specifying tangents. The tangent at a control point \( p_i \) is computed as:

$$ t_i = \frac{1}{2}(p_{i+1} - p_{i-1}) $$

This approach was particularly useful for creating a closed curve, such as a roller coaster track.

### Arc-Length Parameterization
To ensure uniform motion along the curve, Arc-Length Parameterization (ALP) was used. This technique maintains a constant distance (arc-length) traveled per frame, regardless of the spacing between control points.

The process involves:
1. Setting an arc-length value (e.g., 0.01).
2. Moving along the curve in small steps (delta u = 0.001).
3. Recording parameters where the arc-length exceeds the set value.

This method helps in achieving smooth and consistent animation speeds.

### Simulating Speed and Phases
The roller coaster simulation involves four phases:
1. **Lifting the Cart**: The cart is lifted at a constant speed.
2. **Adjusting Initial Speed**: Just before reaching the apex, the cart’s initial speed can be adjusted for a faster start.
3. **Free Fall**: The cart accelerates due to gravity, with speed calculated using the conservation of energy.
4. **Deceleration**: The cart slows down to prepare for the next round, adjusting speed linearly.

### Track Banking
To simulate realistic roller coaster physics, track banking was implemented to counteract centrifugal force, preventing the cart from slipping off. Centripetal acceleration and the effects of gravity are calculated to adjust the track’s angle. To calculate I approximated the second derivative of the curve (track) to get its curvature. Then the tracks are banked to cancel out the sum of gravity force and centrifugal force.

## User Interface
The program's user interface (UI) is designed to be intuitive and flexible, offering various controls for animation and visualization.

### Background Color
The UI allows users to adjust the background color via an RGB selector or a color panel.

### Loading Control Points
Users can load control points from an OBJ file, specifying the filename and pressing the load button. The finite difference bar adjusts the smoothness of the curve.

### Animation Controls
The animation tab offers several adjustable variables:
- **Number of Carts**: Up to 10 carts can be animated.
- **Track Speed (V_lift)**: Modifies the speed during the lifting phase.
- **Initial Speed (V_0)**: Determines the speed push before the cart’s free fall.
- **Delta Time**: Adjusts the speed of animation.
- **Gravity**: Changes the gravity affecting the track dynamics.

### View Options
Three view options are available:
1. **View 1**: Default view with mouse and keyboard navigation.
2. **View 2**: First-person view from the front cart.
3. **View 3**: Spectator view from the ground.

These features ensure a comprehensive and interactive experience for users exploring the roller coaster simulation.

---

This project highlights the integration of mathematical principles and practical implementation in computer animation, showcasing the creation of a smooth, realistic roller coaster simulation.
