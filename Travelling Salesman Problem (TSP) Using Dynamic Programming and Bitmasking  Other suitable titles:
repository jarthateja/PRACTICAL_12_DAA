#include <iostream>
#include <algorithm>
using namespace std;

#define INF 999999

int n;
int cost[10][10];
int dp[1 << 10][10];

int tsp(int mask, int pos)
{
    // If all cities are visited
    if (mask == (1 << n) - 1)
        return cost[pos][0];

    if (dp[mask][pos] != -1)
        return dp[mask][pos];

    int ans = INF;

    // Visit an unvisited city
    for (int city = 0; city < n; city++)
    {
        if ((mask & (1 << city)) == 0)
        {
            int newAns = cost[pos][city] +
                         tsp(mask | (1 << city), city);

            ans = min(ans, newAns);
        }
    }

    return dp[mask][pos] = ans;
}

int main()
{
    cout << "Enter number of cities: ";
    cin >> n;

    cout << "Enter cost matrix:\n";

    for (int i = 0; i < n; i++)
    {
        for (int j = 0; j < n; j++)
        {
            cin >> cost[i][j];
        }
    }

    fill(&dp[0][0], &dp[0][0] + (1 << 10) * 10, -1);

    cout << "Minimum travelling cost: "
         << tsp(1, 0) << endl;

    return 0;
}
