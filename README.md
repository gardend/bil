# Билеты по алгоритмике

## Билет 1. Сортирвка пузырьком. issorted, sortperm!, sort!. Сортирвка по значению функции. 
Сортировка пузырьком:
```julia
function bubblesort!(a)
    n = length(a)
    for k in 1:n-1
        is_sorted = true
        for i in 1:n-k
            if a[i]>a[i+1]
                a[i], a[i+1] = a[i+1], a[i]
                is_sorted = false
            end
        end
        if is_sorted
            break
        end
    end
    return a
end
```
Индексация после сортировки пузырьком:
```julia
function bubblesortperm!(a)
    n = length(a)
    indexes = collect(1:n)
    for k in 1:n-1
        is_sorted = true
        for i in 1:n-k
            if a[i] > a[i+1]
                a[i], a[i+1] = a[i+1], a[i]
                indexes[i], indexes[i+1] = indexes[i+1], indexes[i]
                is_sorted = false
            end
        end
        if is_sorted
            break
        end
    end
    return indexes
end
```
issorted - функция, возвращающая true или false в зависимости от того, отсортирован вектор или нет
  issorted(v, lt=isless, by=identity, rev:Bool=false, order::Ordering=Forward)
  Пример:
  julia> issorted([1, 2, 3])
  true

  julia> issorted([(1, "b"), (2, "a")], by = x -> x[1])
  true

  julia> issorted([(1, "b"), (2, "a")], by = x -> x[2])
  false

  julia> issorted([(1, "b"), (2, "a")], by = x -> x[2], rev=true)
  true
