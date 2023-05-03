Download Link: https://assignmentchef.com/product/solved-cs1566-project-1-transformation-with-trackball
<br>
The purpose of this project is for you to transform (rotate and scale) an object in three dimensional space using a mouse.

Part I: 3D Objects

For this project, you need to create a computer generated three-dimensional object where each surface (triangle) of the object has a random color. For best result, the center of these objects must be at the origin. The maximum score of this part is 40 points. The score of this part will be based on the difficulty of the object you decide to create as follows:

<ul>

 <li>Cone: 15 Points</li>

 <li>Cylinder: 20 Points</li>

 <li>Tube: 25 Points</li>

 <li>Sphere: 30 Points</li>

 <li>Torus: 35 Points</li>

 <li>Spring: 40 Points Here are examples:</li>

</ul>

<h1>Zoom In and Zoom Out</h1>

For this project, we will use the scroll wheel of a mouse to scale an object. Scroll one way is an equivalent of enlarge an object in all direction about the origin by the factor of 1.02. Similarly, to shrink the object by the factor of 1/1.02 can be done by scrolling the other way.

Scrolling events are the same as mouse event. So, you need to call the glutMouseFunc() function to register your callback function:

glutMouseFunc(mouse);

where your mouse() function should look like the following:

<table width="623">

 <tbody>

  <tr>

   <td width="623">void mouse(int button, int state, int x, int y){ :}</td>

  </tr>

 </tbody>

</table>

If you scroll up, the mouse() function will be call with the variable button initialized to 3. Similarly, if you scroll down, the variable button will be initialized to 4. Simply apply the scaling matrix and call the glutPostRedisplay() function.

<strong>Note </strong>that if you use the track pad of your laptop, it may not registered as a scroll wheel. In this case, use a couple keys on your keyboard to perform zoom in and zoom out instead.

<h1>Trackball Style Rotation </h1>

To rotate an object in 3D, simply imagine that your object is located in the middle of a glass ball. This glass ball can be spun in any direction. Now, imagine that half of this glass ball pops out of your screen as shown below:

<em>y                                                                       y</em>

<em>z</em>

Front View                                           Side View                                Top View

From the above picture, there is a blue cube sitting inside this glass ball. If the glass ball is rotated, this cube is rotated as well.

Note that we a user click a mouse on the screen which is a two-dimensional surface, you have to imagine that the mouse pointer is a finger that touch the glass and point directly to the center of the glass ball in three-dimension. Mouse function only provide your <em>x </em>and <em>y </em>but you have to come up with your imaginary <em>z </em>since it is in three-dimensional space. Here are some examples:

<em>y                                                                       y</em>

<table width="389">

 <tbody>

  <tr>

   <td width="113">Front View</td>

   <td width="185">Side View</td>

   <td width="91"><em>z</em>Top View</td>

  </tr>

  <tr>

   <td width="113"><em>y</em></td>

   <td width="185"><em>y</em></td>

   <td width="91"> </td>

  </tr>

 </tbody>

</table>

<table width="389">

 <tbody>

  <tr>

   <td width="113"> </td>

   <td width="185"> </td>

   <td width="91"><em>z</em></td>

  </tr>

  <tr>

   <td width="113">Front View</td>

   <td width="185">Side View</td>

   <td width="91">Top View</td>

  </tr>

 </tbody>

</table>

<em>y                                                                       y</em>

<em>z</em>

Front View                                           Side View                                Top View

To rotate the object inside this class ball, user needs to simply move his/her finger while touching the ball. For this project, assume that a user’s finger is always point directly to the origin while it is moving. Ideally, a user can twist his/her finger to rotate the glass ball. But since we cannot twist the mouse pointer, we assume that twisting the finger is not allow for this project. We will use left button of a mouse to simulate a user touches the glass ball. If the left button is down, user touches the ball at the current pointer position. If the left button is up, user released his/her finger from the ball. To capture the left button event, we use the same callback as in previous section. The variable button will be initialized to GLUT LEFT BUTTON and the variable state will be initialized to either GLUT UP or GLUT DOWN. The variables x and y will be set to the pointer position. <strong>Note </strong>that the pointer position is the screen position. The top-left corner of the screen is at (0<em>,</em>0).

If the mouse pointer is moving while the left button is down, it simulates a user turning the glass ball. When the glass ball rotates, it rotates about a vector and the fixed point of rotation is at the origin. Your job is to come up with the vector so that you can apply rotation matrices correctly. A method of calculating this vector will be discussed in class.

To capture mouse motion events, use the glutMotionFunc() function as shown below:

glutMotionFunc(motion);

and the motion() function should look like the following:

<table width="623">

 <tbody>

  <tr>

   <td width="623">void motion(int x, int y){ :}</td>

  </tr>

 </tbody>

</table>

The variables x and y will be set to the current pointer position.

<h1>Spinning an Object (Just for fun)</h1>

One special feature of this glass ball is that it can rotate indefinitely (no friction). If a user touches the glass ball, drags his/her finger, and releases the finger, the glass ball should spin in the same direction of the user’s finger indefinitely. <strong>Note </strong>that the zoom-in/zoom-out feature must work while the object is spinning indefinitely.