# MATH 550: Numerical PDEs - Homework 1

## Project Structure

```
MATH550-HW0/
├── README.md
├── code/
│   ├── problem1.ipynb
│   └── problem3.ipynb
└── writeup/
    ├── MATH550_HW1.md
    └── figs/
        ├── Problem1.png
        ├── Problem2.png
        └── Problem3.png
```

## Files

| Path | Description |
|------|-------------|
| `writeup/MATH550_HW1.md` | Homework submission |
| `code/problem1.ipynb` | Problems 1–2: Stokes equation with manufactured solutions with solution and convergence plots |
| `code/problem3.py` | Problem 3: Darcy Stokes equation with solution plot |
| `writeup/figs/Problem1.png` | Solution plot for Problem 1 |
| `writeup/figs/Problem2.png` | Error Plot |
| `writeup/figs/Problem3.png` | Darcy Stokes Equation |

## Running the Code

```bash 
pip install numpy scipy matplotlib
pip install cmocean
jupyter nbconvert --execute problem1.ipynb
jupyter nbconvert --execute problem3.ipynb
```