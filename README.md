#include <bits/stdc++.h>
using namespace std;

vector<vector<int>> threesum(vector<int>& nums) {
    int n = nums.size();
    if (n < 3) {
        return {};
    }
    vector<vector<int>> result;
    sort(nums.begin(), nums.end());

    for (int i = 0; i < n; i++) {
        if (i == 0 || nums[i] != nums[i - 1]) {
            int left = i + 1;
            int right = n - 1;

            while (left < right) {
                int sum = nums[i] + nums[left] + nums[right];
                if (sum == 0) {
                    result.push_back({nums[i], nums[left], nums[right]});
                    while (left < right && nums[left] == nums[left + 1]) left++; 
                    while (left < right && nums[right] == nums[right - 1]) right--;
                    left++;
                    right--;
                } else if (sum > 0) {
                    right--;
                } else {
                    left++;
                }
            }
        }
    }

    return result;
}

int main() {
    int n;
    cin >> n;
    vector<int> nums(n);
    for (int i = 0; i < n; i++) {
        cin >> nums[i];
    }

    vector<vector<int>> check = threesum(nums);
    for (const auto& x : check) {
        cout << "Bo ba phan tu do la: [" << x[0] << " " << x[1] << " " << x[2] << "]" << endl;
    }

    return 0;
}
