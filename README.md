# IETL
for IETL testing
class Solution {
    public int solution(int[] A) {
        int N = A.length;
        int maxSum = 0;

        for (int i = 0; i < N; i++) {
            A[i] = Math.abs(A[i]);
            maxSum += A[i];
        }

        boolean[] possibleSums = new boolean[maxSum + 1];
        possibleSums[0] = true;

        for (int i = 0; i < N; i++) {
            for (int j = maxSum; j >= A[i]; j--) {
                possibleSums[j] = possibleSums[j] || possibleSums[j - A[i]];
            }
        }

        int minVal = maxSum;
        for (int i = 0; i <= maxSum / 2; i++) {
            if (possibleSums[i]) {
                minVal = Math.min(minVal, maxSum - 2 * i);
            }
        }

        return minVal;
    }
}
