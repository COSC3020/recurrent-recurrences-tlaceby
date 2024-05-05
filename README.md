[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/8KYthzwp)

# Recurrent Recurrences

Give big $\Theta$ bounds for the following recurrence relations.

1.  $$
        T(n) =
            \begin{cases}
                1 & n \leq 1\\
                T\left(\frac{n}{13}\right) + 5 & n > 1
            \end{cases}
    $$

Each step divides $n$ by 13.

At step $i$: $n / 13^i \leq 1$
This implies $13^i \geq n$
Using logarithms to simplify: $i \log(13) \geq \log(n)$.

Thus, $i \geq \frac{\log(n)}{\log(13)}$

Therefore $i = \log_{13} n$. Each recursive step adds a constant overhead of 5, so the total cost will be:

$T(n) = 5i$ where $i = \log_{13} n$
Hence, $T(n) = 5 \log_{13} n \approx \Theta(\log n)$

2.  $$
    T(n) =
        \begin{cases}
            1 & n \leq 1\\
            13 T\left(\frac{n}{13}\right) + 5 & n > 1
        \end{cases}
    $$

3.  $$
    T(n) =
        \begin{cases}
            1 & n \leq 1\\
            13 T\left(\frac{n}{13}\right) + 2n & n > 1
        \end{cases}
    $$
