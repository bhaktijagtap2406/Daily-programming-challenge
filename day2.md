##Question
You are given an array arr containing n+1 integers, where each integer is in the range [1, n] inclusive. There is exactly one duplicate number in the array, but it may appear more than once. Your task is to find the duplicate number without modifying the array and using constant extra space.

##answer
#include <iostream>
#include <vector>
using namespace std;

int findDuplicate(vector<int>& arr) {
    int a = arr[0];  // walker (1 step at a time)
    int b = arr[0];  // runner (2 steps at a time)

    // Step 1: meet inside the cycle
    do {
        a = arr[a];        // move 1 step
        b = arr[arr[b]];   // move 2 steps
    } while (a != b);

    // Step 2: find the duplicate
    a = arr[0];
    while (a != b) {
        a = arr[a];
        b = arr[b];
    }

    return a;  // duplicate number
}

int main() {
    vector<int> arr = {1, 3, 4, 2, 2};
    cout << "Duplicate number: " << findDuplicate(arr) << endl;
    return 0;
}
