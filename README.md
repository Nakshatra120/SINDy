# Sparse Identification of Nonlinear Dynamics (SINDy) – Lorenz System Example

This repository demonstrates how to extract **low-dimensional governing equations** directly from time-series data using the [SINDy algorithm](https://www.pnas.org/doi/10.1073/pnas.1517384113).  
The example focuses on the **Lorenz system**, a chaotic three-dimensional dynamical system, but the framework is general and can be applied to a wide range of physical and biological problems.

---

## ✨ Motivation

Complex systems often produce high-dimensional time-series data.  
But in many cases, the underlying dynamics can be described by a **small number of equations with only a few terms**.  

The SINDy method automates the discovery of these equations:  
1. Generate or collect time-series data.  
2. Build a library of candidate nonlinear functions (e.g., polynomials).  
3. Use sparse regression to select only the most important terms.  
4. Recover the governing equations of the system.  

---

## 📚 Applications

SINDy has been applied to a variety of domains, including:  
- 🧠 **Neuroscience** – extracting neural population dynamics.  
- 🌍 **Climate science** – reduced-order models for weather and climate.  
- 🧪 **Biology** – epidemic models, population dynamics.  
- 📈 **Finance** – identifying simplified models of market dynamics.  
- 🌀 **Fluid dynamics** – discovering Navier–Stokes approximations.  

---

## 🛠 Repository Structure

```
sindy-lorenz/
│── README.md               # Project description, usage, references
│── requirements.txt        # Python dependencies
│── src/                    # Core implementation
│   ├── library.py          # Function to build candidate polynomial library
│   ├── optimizer.py        # Sparse regression (LASSO, thresholding)
│   ├── simulate.py         # Lorenz system simulator (using solve_ivp)
│   └── sindy.py            # Main pipeline tying everything together
│── notebooks/              
│   ├── 01_generate_data.ipynb    # Simulate Lorenz trajectories
│   ├── 02_build_library.ipynb    # Construct polynomial features
│   ├── 03_fit_sindy.ipynb        # Apply sparse regression, recover equations
│   └── 04_applications.ipynb     # Additional toy examples
│── examples/
│   └── figures/            # Generated plots (Lorenz attractor, predictions)
│── LICENSE
```

---

## 🚀 Quickstart

### 1. Clone the repo
```bash
git clone https://github.com/<your-username>/sindy-lorenz.git
cd sindy-lorenz
```

### 2. Install dependencies
```bash
pip install -r requirements.txt
```

### 3. Run the notebooks
Start with the first notebook:
```bash
jupyter notebook notebooks/01_generate_data.ipynb
```

Follow the workflow in order:  
1. Generate Lorenz time-series.  
2. Build polynomial library.  
3. Fit sparse regression.  
4. Compare discovered vs true equations.  

---

## 📊 Example Result

After running the full pipeline, the discovered system should approximate the Lorenz equations:

\[
\dot{x} \approx \sigma (y - x), \quad
\dot{y} \approx x(\rho - z) - y, \quad
\dot{z} \approx xy - \beta z
\]

with coefficients very close to the true parameters \((\sigma=10, \rho=28, \beta=8/3)\).

*Placeholder for figure: reconstructed vs true Lorenz attractor.*

---

## 🔮 Future Directions

- Extend to other dynamical systems (pendulum, double pendulum, epidemic models).  
- Explore alternative libraries (Fourier, radial basis functions).  
- Test different sparse optimization algorithms (hard thresholding, LASSO, sequential thresholded least squares).  

---

## 📖 References

- Brunton, S. L., Proctor, J. L., & Kutz, J. N. (2016).  
  *Discovering governing equations from data by sparse identification of nonlinear dynamical systems*.  
  PNAS, 113(15), 3932–3937. [DOI:10.1073/pnas.1517384113](https://www.pnas.org/doi/10.1073/pnas.1517384113)

---

## 🙌 Acknowledgements

This repo was created as a personal exploration of the SINDy algorithm and its applications to physics and beyond.  
Contributions and suggestions are welcome!
