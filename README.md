# Rust
Test Programs In Rust Programming Language

1. Implement a function that checks whether a given string is a palindrome or not
```
fn is_palindrome(s: &str) -> bool {
    let reversed: String = s.chars().rev().collect();
    s == reversed
}

fn main() {
    let test_string1 = "radar";
    println!("Is '{}' a palindrome? {}", test_string1, is_palindrome(test_string1));
}
```
 2.Given a sorted array of integers, implement a function that returns the index of the first occurrence of a given number.
 ```
fn find_first_occurrence(nums: &[i32], target: i32) -> Option<usize> {
    nums.iter().position(|&x| x == target)
}

fn main() {
    let nums = vec![1, 2, 3, 4, 4, 4, 5, 6];
    let target = 4;
    if let Some(index) = find_first_occurrence(&nums, target) {
        println!("The first occurrence of {} is at index {}", target, index);
    } else {
        println!("{} not found in the array", target);
    }
}

```
 3.Given a string of words, implement a function that returns the shortest word in the string.
```
fn shortest_word(s: &str) -> Option<&str> {
    s.split_whitespace().min_by_key(|word| word.len())
}

fn main() {
    let sentence = "This is a test sentence";
    if let Some(shortest) = shortest_word(sentence) {
        println!("The shortest word is: {}", shortest);
    } else {
        println!("No words found in the string");
    }
}
```

 4.Implement a function that checks whether a given number is prime or not.
 ```
fn is_prime(num: u32) -> bool {
    if num <= 1 {
        return false;
    }
    for i in 2..=(num / 2) {
        if num % i == 0 {
            return false;
        }
    }
    true
}

fn main() {
    let num = 17;
    if is_prime(num) {
        println!("{} is prime", num);
    } else {
        println!("{} is not prime", num);
    }
}
```
 5. Given a sorted array of integers, implement a function that returns the median of the array
```
fn find_median(nums: &[i32]) -> f64 {
    let len = nums.len();
    if len % 2 == 0 {
        let mid = len / 2;
        (nums[mid - 1] + nums[mid]) as f64 / 2.0
    } else {
        nums[len / 2] as f64
    }
}

fn main() {
    let nums = vec![1, 2, 3, 4, 5];
    println!("The median of the array is: {}", find_median(&nums));
}
```
 6. Implement a function that finds the longest common prefix of a given set of strings.
```
fn longest_common_prefix(strings: &[&str]) -> String {
    if strings.is_empty() {
        return String::new();
    }
    let mut prefix = String::new();
    for (i, ch) in strings[0].chars().enumerate() {
        if strings.iter().all(|&s| s.chars().nth(i) == Some(ch)) {
            prefix.push(ch);
        } else {
            break;
        }
    }
    prefix
}

fn main() {
    let words = vec!["flower", "flow", "flight"];
    println!("The longest common prefix is: {}", longest_common_prefix(&words));
}
```
 7. Implement a function that returns the kth smallest element in a given array.
```
fn kth_smallest(nums: &[i32], k: usize) -> Option<i32> {
    let mut sorted_nums = nums.to_vec();
    sorted_nums.sort();
    sorted_nums.get(k - 1).cloned()
}

fn main() {
    let nums = vec![3, 1, 4, 1, 5, 9, 2, 6];
    let k = 3;
    if let Some(kth) = kth_smallest(&nums, k) {
        println!("The {}th smallest element is: {}", k, kth);
    } else {
        println!("Array is too small or k is out of bounds");
    }
}
```
 8. Given a binary tree, implement a function that returns the maximum depth of the tree.
```
// Assuming a binary tree node structure like this:
// struct TreeNode {
//     val: i32,
//     left: Option<Box<TreeNode>>,
//     right: Option<Box<TreeNode>>,
// }

fn max_depth(root: Option<&Box<TreeNode>>) -> i32 {
    match root {
        Some(node) => {
            let left_depth = max_depth(node.left.as_ref());
            let right_depth = max_depth(node.right.as_ref());
            1 + left_depth.max(right_depth)
        }
        None => 0,
    }
}
```
 9. Reverse a string in Rust
```     
fn reverse_string(s: &str) -> String {
    s.chars().rev().collect()
}

fn main() {
    let s = "hello";
    println!("Reversed string: {}", reverse_string(s));
}
```
 10. Check if a number is prime in Rust
```
fn is_prime(num: u32) -> bool {
    if num <= 1 {
        return false;
    }
    for i in 2..=(num / 2) {
        if num % i == 0 {
            return false;
        }
    }
    true
}

fn main() {
    let num = 17;
    if is_prime(num) {
        println!("{} is prime", num);
    } else {
        println!("{} is not prime", num);
    }
}
```
11. Merge two sorted arrays in Rust
```
fn merge_sorted_arrays(arr1: &[i32], arr2: &[i32]) -> Vec<i32> {
    let mut merged = Vec::with_capacity(arr1.len() + arr2.len());
    let mut i = 0;
    let mut j = 0;
    while i < arr1.len() && j < arr2.len() {
        if arr1[i] < arr2[j] {
            merged.push(arr1[i]);
            i += 1;
        } else {
            merged.push(arr2[j]);
            j += 1;
        }
    }
    merged.extend_from_slice(&arr1[i..]);
    merged.extend_from_slice(&arr2[j..]);
    merged
}

fn main() {
    let arr1 = vec![1, 3, 5, 7];
    let arr2 = vec![2, 4, 6, 8];
    let merged = merge_sorted_arrays(&arr1, &arr2);
    println!("Merged array: {:?}", merged);
}
```
 12. Find the maximum subarray sum in Rust
```
fn max_subarray_sum(nums: &[i32]) -> i32 {
    let mut max_sum = 0;
    let mut current_sum = 0;
    for num in nums {
        current_sum = (current_sum + num).max(0);
        max_sum = max_sum.max(current_sum);
    }
    max_sum
}

fn main() {
    let nums = vec![-2, 1, -3, 4, -1, 2, 1, -5, 4];
    println!("Maximum subarray sum: {}", max_subarray_sum(&nums));
}
```

