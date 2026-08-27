# JAVASCRIPT-BASED DRAWING APPLICATION

## AIM

To develop a JavaScript-based drawing application using HTML5 Canvas to draw shapes such as Line, Rectangle, and Circle.

## ALGORITHM

1. Create an HTML page.
2. Add a `<canvas>` element to create the drawing area.
3. Add a drop-down list to select the shape (Line, Rectangle, or Circle).
4. Obtain the canvas context using `getContext("2d")`.
5. Capture the starting coordinates when the mouse button is pressed (`mousedown`).
6. Capture the ending coordinates when the mouse button is released (`mouseup`).
7. Determine the selected shape from the drop-down list.
8. Draw the selected shape:
   - Use `moveTo()` and `lineTo()` for a line.
   - Use `strokeRect()` for a rectangle.
   - Use `arc()` for a circle.
9. Display the drawn shape on the canvas.

## PROGRAM
~~~
<!DOCTYPE html>
<html>
    <head>
        <title>canvas</title>
        <style>
            canvas {
                border: 2px solid black;
                background-color: white;
                display: block;
                margin-top: 10px;
            }
        </style>
    </head>
    <body>
        <select id="shape">
            <option value="Line">Line</option>
            <option value="Rectangle">Rectangle</option>
            <option value="Circle">Circle</option>
        </select>

        <canvas id="canvas" height="500" width="500"></canvas>

        <script>
            let canvas = document.getElementById("canvas");
            let ctx = canvas.getContext("2d");
            let x, y;

            canvas.addEventListener("mousedown", function(e) {
                x = e.offsetX;
                y = e.offsetY;
            });

            canvas.addEventListener("mouseup", function(e) {
                let endx = e.offsetX;
                let endy = e.offsetY;
                let shape = document.getElementById("shape").value;

                if (shape === "Line") {
                    ctx.beginPath();
                    ctx.moveTo(x, y);
                    ctx.lineTo(endx, endy);
                    ctx.stroke();
                } else if (shape === "Rectangle") {
                    ctx.beginPath();
                    ctx.strokeRect(x, y, endx - x, endy - y);
                } else if (shape === "Circle") {
                    let radius = Math.sqrt(Math.pow((endx - x), 2) + Math.pow((endy - y), 2));
                    ctx.beginPath();
                    ctx.arc(x, y, radius, 0, Math.PI * 2);
                    ctx.stroke();
                }
            });
        </script>
    </body>
</html>
~~~

## OUTPUT



## RESULT

A JavaScript-based drawing application was successfully developed using HTML5 Canvas. The application enables users to draw Lines, Rectangles, and Circles interactively using mouse events.

