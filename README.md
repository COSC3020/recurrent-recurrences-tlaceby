[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/8iYthzwp)

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
Therefore, $T(n) = 5 \log_{13} n \approx \Theta(\log n)$

2.  $$
    T(n) =
        \begin{cases}
            1 & n \leq 1\\
            13 T\left(\frac{n}{13}\right) + 5 & n > 1
        \end{cases}
    $$

We apply similar logic for the recursion depth $i = \log_{13} n$. However each step scales the prior result by 13 and adds 5.

$T(n) = 13T\left(\frac{n}{13}\right) + 5$

Substituting iteratively, we get $T(n) = 13^i + 5 \cdot (1 + 13 + 13^2 + \dots + 13^{i-1})$.

This sum is a geometric series, which simplifies to $5 \frac{13^i - 1}{12}$.

Since $13^i$ grows with n, $13^i \approx n$, $T(n) \approx \Theta(n)$.

3.  $$
    T(n) =
        \begin{cases}
            1 & n \leq 1\\
            13 T\left(\frac{n}{13}\right) + 2n & n > 1
        \end{cases}
    $$

In this recurrence, each step includes a term linearly dependent on $n$, which will dominate the cost as the recursion unfolds.

$T(n) = 13T\left(\frac{n}{13}\right) + 2n$.

$T\left(\frac{n}{13}\right) = 13T\left(\frac{n}{13^2}\right) + 2 \frac{n}{13}$.

$T(n) = 13^2 T\left(\frac{n}{13^2}\right) + 13 \cdot 2 \frac{n}{13} + 2n$.

$T(n) = 13^2 T\left(\frac{n}{13^2}\right) + 2n \cdot (1 + 13)$.

$T(n) = 13^k + 2n (1 + 13 + 13^2 + \dots + 13^{k-1})$.
This simplifies to $2n \frac{13^k - 1}{12}$.

As $13^k \approx n$, the dominating term turns out to be $2n \cdot \frac{n - 1}{12} \approx 2n \cdot \frac{n}{12} = \frac{n^2}{6}$

Thus $T(n) = \Theta(n^2)$ due to the presence of $2n$ scaling with each recursive expansion.

## External Resources

- https://www.geeksforgeeks.org/substitution-method-to-solve-recurrence-relations/
- My Discrete Textbook from a year ago: **Discrete Mathematics : An open Introduction (Oscar Levin) 3rd Edition** Pages 167 - 177 and some notes on solving recurrence relations and sequences.
- Also used GPT with help with formatting and cleaning up my explaination.
