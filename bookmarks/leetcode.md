# 🎯 LeetCode Problems Bookmarks

Bộ sưu tập các bài LeetCode quan trọng và hay gặp trong phỏng vấn.

## 📊 Thống kê

- **Tổng số bài:** 2
- **Easy:** 1
- **Medium:** 1
- **Hard:** 0

---

## Easy

### 1. Two Sum

**Link:** [LeetCode #1 - Two Sum](https://leetcode.com/problems/two-sum/)

**Độ khó:** 🟢 Easy

**Mô tả:**
Cho một mảng các số nguyên `nums` và một số nguyên `target`, trả về indices của hai số sao cho tổng của chúng bằng `target`.

**Ví dụ:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: nums[0] + nums[1] = 2 + 7 = 9
```

**Giải pháp:**

<details>
<summary>JavaScript - Hash Map (O(n))</summary>

```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  const map = new Map();

  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];

    if (map.has(complement)) {
      return [map.get(complement), i];
    }

    map.set(nums[i], i);
  }

  return [];
};
```

**Độ phức tạp:**

- Time: O(n)
- Space: O(n)
</details>

<details>
<summary>PHP - Hash Map</summary>

```php
class Solution {
    /**
     * @param Integer[] $nums
     * @param Integer $target
     * @return Integer[]
     */
    function twoSum($nums, $target) {
        $map = [];

        foreach ($nums as $i => $num) {
            $complement = $target - $num;

            if (isset($map[$complement])) {
                return [$map[$complement], $i];
            }

            $map[$num] = $i;
        }

        return [];
    }
}
```

</details>

**Tags:** `Array`, `Hash Table`, `Two Pointers`

**Lưu ý:**

- Đây là bài cơ bản nhất, thường được hỏi để warm-up
- Giải pháp tối ưu sử dụng Hash Map
- Cần chú ý trường hợp edge case: mảng rỗng, không có solution

---

## Medium

### 2. Add Two Numbers

**Link:** [LeetCode #2 - Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

**Độ khó:** 🟡 Medium

**Mô tả:**
Cho hai linked list không rỗng đại diện cho hai số nguyên không âm. Các chữ số được lưu trữ theo thứ tự ngược lại và mỗi node chứa một chữ số. Cộng hai số và trả về tổng dưới dạng linked list.

**Ví dụ:**

```
Input: l1 = [2,4,3], l2 = [5,6,4]
Output: [7,0,8]
Explanation: 342 + 465 = 807
```

**Giải pháp:**

<details>
<summary>JavaScript - Linked List Traversal</summary>

```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
var addTwoNumbers = function (l1, l2) {
  const dummy = new ListNode(0);
  let current = dummy;
  let carry = 0;

  while (l1 !== null || l2 !== null || carry !== 0) {
    const val1 = l1 ? l1.val : 0;
    const val2 = l2 ? l2.val : 0;

    const sum = val1 + val2 + carry;
    carry = Math.floor(sum / 10);

    current.next = new ListNode(sum % 10);
    current = current.next;

    if (l1) l1 = l1.next;
    if (l2) l2 = l2.next;
  }

  return dummy.next;
};
```

**Độ phức tạp:**

- Time: O(max(m, n)) - m và n là độ dài của l1 và l2
- Space: O(max(m, n)) - cho linked list kết quả
</details>

<details>
<summary>PHP - Linked List</summary>

```php
/**
 * Definition for a singly-linked list.
 * class ListNode {
 *     public $val = 0;
 *     public $next = null;
 *     function __construct($val = 0, $next = null) {
 *         $this->val = $val;
 *         $this->next = $next;
 *     }
 * }
 */
class Solution {
    /**
     * @param ListNode $l1
     * @param ListNode $l2
     * @return ListNode
     */
    function addTwoNumbers($l1, $l2) {
        $dummy = new ListNode(0);
        $current = $dummy;
        $carry = 0;

        while ($l1 !== null || $l2 !== null || $carry !== 0) {
            $val1 = $l1 ? $l1->val : 0;
            $val2 = $l2 ? $l2->val : 0;

            $sum = $val1 + $val2 + $carry;
            $carry = intdiv($sum, 10);

            $current->next = new ListNode($sum % 10);
            $current = $current->next;

            if ($l1) $l1 = $l1->next;
            if ($l2) $l2 = $l2->next;
        }

        return $dummy->next;
    }
}
```

</details>

**Tags:** `Linked List`, `Math`, `Recursion`

**Lưu ý:**

- Chú ý xử lý carry (số nhớ)
- Xử lý trường hợp hai linked list khác độ dài
- Sử dụng dummy node để dễ xử lý
- Cẩn thận với carry ở cuối (ví dụ: 99 + 1 = 100)

---

## 📚 Tài nguyên tham khảo

- [LeetCode Patterns](https://seanprashad.com/leetcode-patterns/)
- [NeetCode](https://neetcode.io/) - Video giải thích chi tiết
- [LeetCode Solutions GitHub](https://github.com/azl397985856/leetcode)

---

## 🎯 Mẹo làm bài LeetCode

1. **Đọc kỹ đề bài** - Xác định input, output, constraints
2. **Brainstorm giải pháp** - Brute force → Optimize
3. **Phân tích độ phức tạp** - Time & Space complexity
4. **Code & Test** - Viết code rõ ràng, test với các test case
5. **Tối ưu hóa** - Có thể cải thiện được không?

---

⭐ **Happy Coding!** ⭐
