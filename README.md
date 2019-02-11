# Udp Remote Control - Joystick
This project aims to develop an android APP to control a remote car which take the linear and angular wheel velocities for both left and right side. The APP provides a joystick UI allowing easy control of the remote car's position and a scroll bar to control the car's orientation (heading). The wireless communication protocol can be either TCP or UDP.

## Joystick
**Joystick Initialization**
First, you will need to implement a custom view. It can be achieve by overriding **onDraw**.
The **onDraw** function is called whenever the view should render its content. The following codes make up the joystick UI.
- Draw the main circle (largest) by calling **canvas.drawCircle** where the radius is defined to the joystick radius.
- Draw the secodary circle and set it to be half of the joystick radius.
- Draw the axis of the joystick circle by calling **canvas.drawLine**
- Draw a red button representing the center of the joystick, it should follow the movement of the user.
```
// Main circle
mainCircle = new Paint(Paint.ANTI_ALIAS_FLAG);
mainCircle.setColor(Color.WHITE);
mainCircle.setStyle(Paint.Style.FILL_AND_STROKE);

// Secondary circle
secondaryCircle = new Paint();
secondaryCircle.setColor(Color.GREEN);
secondaryCircle.setStyle(Paint.Style.STROKE);

// Axis
verticalLine = new Paint();
verticalLine.setStrokeWidth(5);
verticalLine.setColor(Color.RED);
horizontalLine = new Paint();
horizontalLine.setStrokeWidth(2);
horizontalLine.setColor(Color.BLACK);

//Button
button = new Paint(Paint.ANTI_ALIAS_FLAG);
button.setColor(Color.RED);
button.setStyle(Paint.Style.FILL);
```
