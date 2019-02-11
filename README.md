# Udp Remote Control - Joystick
This project aims to develop an android APP to control a remote car which take the linear and angular wheel velocities for both left and right side. The APP provides a joystick UI allowing easy control of the remote car's position and a scroll bar to control the car's orientation (heading). The wireless communication protocol can be either TCP or UDP.

## Joystick
### Joystick View

First, you will need to implement a custom view. 
```
public class JoystickView extends View implements  Runnable{...}
```

### Joystick Initialization
The following codes initialize the joystick UI.
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
### Registration of events
The following fucntions will be called when a certain event is triggered.
**onSizeChanged**: Called when the size of the view has changed. It is used to define the button radius and joystick radius.
```
    @Override
    //This is called when the size of the view has changed
    protected void onSizeChanged(int xNew, int yNew, int xOld, int yOld) {
        super.onSizeChanged(xNew, yNew, xOld, yOld);
        // before measure, get the center of view
        xPosition = (int) getWidth() / 2;
        yPosition = (int) getWidth() / 2;
        int d = Math.min(xNew, yNew);
        buttonRadius = (int) (d / 2 * 0.25);
        joystickRadius = (int) (d / 2 * 0.75);
    }
```
**onMeasure**: 

**onTouchEvent**: Called when a touch screen motion event occurs so the position information of the touch spot is obtained.

**onDraw**: The **onDraw** function is called whenever the view should render its content. 

**getAngle**: Return the joystick angle with respect to the center

**getPower**: Return the power(amplitiude) from the joystick (ranges from 0-100)

**getDirection**: 
