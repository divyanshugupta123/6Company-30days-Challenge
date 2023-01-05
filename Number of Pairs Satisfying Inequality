class Solution {
    public long numberOfPairs(int[] nums1, int[] nums2, int diff) {
        int n = nums1.length;
        int[] v = new int[n];
        for(int i = 0; i < n; i++) {
            v[i] = nums1[i] - nums2[i] + 30_001;
        }
        
        BIT tree = new BIT();
        for(int i = n - 1; i >= 0; i--) {
            tree.update(v[i] + diff, 1);
        }
        long ans = 0;
        for(int i = 0; i < n - 1; i++) {
            tree.update(v[i] + diff, -1);
            int cnt = tree.sum(v[i] - 1);
            ans += (n - i - 1) - cnt;
        }
        return ans;
    }
    
    private static class BIT {
        int[] arr = new int[60_003];
        
        public int sum(int v) {
            int sum = 0;
            while(v > 0) {
                sum += arr[v];
                v -= v & (-v);
            }
            return sum;
        }
        
        public void update(int v, int cnt) {
            while(v < arr.length) {
                arr[v] += cnt;
                v += v & (-v);
            }
        }
    }
}
