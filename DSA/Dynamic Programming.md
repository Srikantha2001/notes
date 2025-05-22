

## Partition DP

- Mainly used to solve problems involving partitioning the entire array
- This DP pattern is mainly used where the <mark style="background: #FFB8EBA6;">order of operation</mark> is important

input : usually an array
expected output : best way to partition the array to optimize a condition


**RECURSIVE CODE**

```Java
public T getOptimalValue(int [] arr, int left, int right) {
	// normally basecase is left == right
	if(baseCase) {
		return baseValue
	}

	// need to verify all the paritions between left to right
	T finalOptimalValue, tempOptimalValue;
	for(int mid=left,mid<right;mid++){
		leftPartitionValue = getOptimalValue(arr, left, mid);
		rightPartitionValue = getOptimalValue(arr, mid+1, right);

		tempOptimalValue = function(leftPartitionValue, rightPartitionValue, left, right, mid);
		finalOptimalValue = chooseOptimal(finalOptimalValue, tempOptimalValue);
	}
	return finalOptimalValue;
}
```

**MEMOIZED CODE**

```Java
public T getOptimalValue(int [] arr, int left, int right, T [][] dp) {
	// normally basecase is left == right
	if(base_case ) {
		return value
	}
	if(dp[left][right] != default) return dp[left][right];

	// need to verify all the paritions between left to right
	T finalOptimalValue, tempOptimalValue;
	for(int mid=left,mid<right;mid++){
		leftPartitionValue = getOptimalValue(arr, left, mid, dp);
		rightPartitionValue = getOptimalValue(arr, mid+1, right, dp);

		tempOptimalValue = function(leftPartitionValue, rightPartitionValue, left, right, mid);
		finalOptimalValue = chooseOptimal(finalOptimalValue, tempOptimalValue);
	}
	return dp[left][right] = finalOptimalValue;
}
```

**TABULATION CODE**

```Java

public T getOptimalValue(int [] arr) {
	int n = arr.length;
	T [][] dp = new T[n+1][n+1];

	
	// use base case for initialization
	for(int left=N-1;left>=1;left--) {
		for(int right=i+1, right<N;right++){
			T finalOptimalValue, tempOptimalValue;
			for(int mid=left,mid<right;mid++){
				leftPartitionValue = dp[left][mid];
				rightPartitionValue = dp[mid+1][right];
		
				tempOptimalValue = function(leftPartitionValue, rightPartitionValue, left, right, mid);
				finalOptimalValue = chooseOptimal(finalOptimalValue, tempOptimalValue);
			}
			return dp[left][right] = finalOptimalValue;
		}
	}

	dp[1][N];
}
```


PROBLEMS : 

1. Matrix Chain Multiplication : 
2. Minimum Cost to Cut the stick :
3. Burst Balloon :
4. Evaluate Boolean Expression : 
5. Palindrome Partitioning : 
6. Partition array for maximum sum : 
