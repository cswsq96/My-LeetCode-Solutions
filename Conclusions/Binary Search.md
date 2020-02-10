### Find target
```java
public int findTarget(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = (right - left) / 2 + left;
        if (nums[mid] == target) {
            return mid;
        } else if (nums[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}
```

### Find the first element that is greater than target
```java
private int findFirstGreater(int[] nums, int target) {
	int left = 0, right = nums.length - 1;
    while (left <= right) {
      	int mid = (right - left) / 2 + left;
        if (nums[mid] <= target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return left;
}
```

### Find ceiling of a given target (ceiling : the smallest element that is greater than or equal to target)
#### Solution 1
```java
public int findCeiling(int[] nums, int target) {
    int left = 0, right = nums.length - 1;
    while (left < right) {
        int mid = (right - left) / 2 + left;
        if (nums[mid] <= target) {
            left = mid + 1;
        } else {
            right = mid;
        }
    }
    return nums[left] <= target ? left : -1;
}
```
#### Solution 2
```java
public int findCeiling(int[] nums, int target) {
	if (target > nums[nums.length - 1]) return -1;
	
    int left = 0, right = nums.length - 1;
    while (left <= right) {
        int mid = (right - left) / 2 + left;
        if (nums[mid] == target) {
            return nums[mid];
        } else if (nums[mid] < target){
            left = mid + 1;
        } else {
  			right = mid - 1;
		}
    }
    return nums[left];
}
```

### Find floor of a given target (floor : the largest element that is less than or equal to target)
```java
public int findFloor(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        while (left < right) {
            int mid = (right - left) / 2 + left;
            if (nums[mid] == target) {
                return mid;
            }
            if (nums[mid] < target) {
                if (nums[mid+1] > target) {
                    return mid;
                }
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return nums[left] > target ? -1 : left;
    }
}
```
