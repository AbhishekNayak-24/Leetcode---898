# Leetcode---898
Bitwise ORs of Subarrays
//code in java 
import java.util.HashSet;
import java.util.Set;

public class Solution {
    public int subarrayBitwiseORs(int[] arr) {
        Set<Integer> resultORs = new HashSet<>(); // Stores all unique OR values found
        Set<Integer> currentORs = new HashSet<>(); // Stores OR values ending at the current element

        for (int num : arr) {
            Set<Integer> nextORs = new HashSet<>(); // Stores OR values ending at the next element
            
            // Add the current number itself as an OR value
            nextORs.add(num); 
            
            // Calculate ORs by combining the current number with previous currentORs
            for (int val : currentORs) {
                nextORs.add(val | num);
            }
            
            // Update currentORs for the next iteration
            currentORs = nextORs;
            
            // Add all newly found OR values to the overall result set
            resultORs.addAll(currentORs);
        }
        
        return resultORs.size();
    }
}
