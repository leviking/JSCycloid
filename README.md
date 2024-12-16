# Cycloidal Gear Generator

This project is a simple tool to generate an inward-offset epicycloid curve suitable for cycloidal gear designs. By adjusting parameters such as the number of pins, pin radius, and pin circle radius, the tool dynamically creates and displays a cycloidal gear profile. It also provides an option to download the generated gear profile as an SVG.

## Features

- **Dynamic Parameter Adjustment:** Interactively modify the number of pins, pin radius, pin circle radius, and contraction values.  
- **Visual Feedback:** Instantly see the resulting gear shape as an SVG path within the browser.  
- **Custom Offset Calculation:** Generates an inward-offset curve of the epicycloid to accommodate pins, ensuring a more realistic gear tooth profile.  
- **SVG Download:** Export just the gear profile as an SVG file for further processing or manufacturing.

## How It Works

1. **Epicycloid Generation:**  
   The code computes an epicycloid curve based on the given parameters:
   - **Number of Pins (N):** The count of pins the gear meshes with.
   - **Pin Circle Radius (R<sub>pin</sub>):** Radius on which the pins lie.
   - **Contraction (C):** A value to fine-tune the epicycloid profile.
   - **Pin Radius (r<sub>pin</sub>):** Radius of each individual pin.

   Using these inputs, the script calculates:
   - **Rolling Circle Radius (r):** `r = R_pin / N`.
   - **Base Radius (R):** `R = (N - 1) * r`, which defines the underlying epicycloid geometry.

2. **Offset Curve Calculation:**  
   After computing the standard epicycloid points, the code calculates an inward offset curve by:
   - Approximating the tangent vector at each point.
   - Determining the inward-facing normal vector.
   - Shifting the point inward along the normal by the pin radius, resulting in an inset curve that can accommodate the physical pins.

3. **SVG Rendering:**  
   The generated points are converted into an SVG `<path>` element. Reference circles and pins are also drawn for visual context. The viewBox of the SVG is adjusted to frame the gear nicely.

4. **Downloadable Output:**  
   A "Download SVG" button allows you to export just the gear profile (the inward offset epicycloid path) as a clean SVG file.

## Usage

1. **Open `index.html`:**  
   Just open the HTML file in a modern web browser.

2. **Adjust Parameters:**  
   Use the input fields to set:
   - **Number of Pins**
   - **Pin Radius (mm)**
   - **Pin Circle Radius (mm)**
   - **Contraction (mm)**

   Click **"Generate Gear"** to update the drawing.

3. **Download SVG:**  
   Once satisfied with the generated profile, click **"Download SVG (Just Profile)"** to save the current epicycloid outline as an SVG file.

## Customization

You can tweak the code by modifying:
- **Step Size for Derivatives:** `stepDeg` in the JavaScript controls the precision of the offset curve calculation.
- **Visual Appearance:** Adjust CSS or SVG attributes to change stroke colors, widths, or add additional decorative elements.
- **Additional Calculations:** Use the computed curve data for further geometric analyses or integrations into manufacturing workflows.

## License

This project is provided as-is under no specific license. Feel free to use, modify, and integrate it into your own projects. Please note that the resulting gear shapes and designs are subject to the accuracy of the underlying mathematical approximations and should be validated before physical manufacturing.
