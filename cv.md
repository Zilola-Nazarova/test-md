## Code Sample
**Simple Quicksort:** A `partition` method splits an array into smaller and greater elements (with respect to the first element aka `pivot`). Each time I call `partition`, I am sorting two parts of the array with respect to each other. I repeatedly use `partition` on sub-arrays (left and right) to sort an entire array. When `partition` is called on two elements, that sub-array is fully sorted. The first element in any sub-array is used as a pivot. It appears in the middle when combining the two lists together (`resemble` method).

<details>
<summary>SHOW CODE</summary>

```rb
def simple_quicksort(array)
  partition(array)
end

def partition(array)
  pivot = array[0]
  before, after = [], []
  (1..array.length - 1).each do |i|
    if array[i] <= pivot
      before.push(array[i])
    elsif array[i] > pivot
      after.push(array[i])
    end
  end
  before = partition(before) if before.length > 1
  after = partition(after) if after.length > 1
  resemble(before, pivot, after, array)
end

def resemble(before, pivot, after, array)
  index = 0
  array, index = join_part(before, index, array)
  array[index] = pivot
  index += 1
  array, index = join_part(after, index, array)
  array
end

def join_part(part, index, array)
  until part.empty?
    array[index] = part[0]
    index += 1
    part.shift
  end
  [array, index]
end
```
</details>

