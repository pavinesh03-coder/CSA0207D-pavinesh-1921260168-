# C Engine Build Instructions

## Windows

Install a C compiler such as MinGW or MSYS2 GCC, then run:

```powershell
gcc -shared -O2 -o food_matching.dll food_matching.c
```

The Python layer loads the generated DLL through ctypes.

## Linux/macOS

```bash
gcc -shared -fPIC -O2 -o libfood_matching.so food_matching.c
```

## Notes

The matching function uses the formula:

$$
\text{score} = \frac{40 \cdot C + 30 \cdot Q + 20 \cdot L + 10 \cdot U}{100}
$$

where:
- C = category match (0 to 1)
- Q = quantity match (0 to 1)
- L = location match (0 to 1)
- U = urgency score (0 to 1)
