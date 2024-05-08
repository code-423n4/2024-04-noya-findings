### 1) ChainlinkOracleConnector::updateChainlinkPriceAgeThreshold
While the comment reads the threshold should be between 1 day and 10 days, the actual implementation is 1 hours and 10 days.

### 2)  SwapAndBridgeHandler::routes
Incase the maintainer makes a mistake of adding duplicate routes, the state level array will hold the routes for ever as there is no option to remove the entries.
```
  function addRoutes(RouteData[] memory _routes) public onlyMaintainer {
        for (uint256 i = 0; i < _routes.length;) {
            routes.push(_routes[i]);
            emit NewRouteAdded(i, _routes[i].route, _routes[i].isEnabled, _routes[i].isBridge);
            unchecked {
                i++;
            }
        }
    }
```

Solution:
Add ability to remove routes if required.