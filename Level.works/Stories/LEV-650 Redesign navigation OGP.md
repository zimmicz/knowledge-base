## Possible refactoring
- AuthenticatedNavLink should become just `<ShowMeWhen />`
- shared `<Sidebar />` doesn't need to know about `userInfo` and `versionInfo`, these can be provided to children or filtered on in advance
- layouts can be used to show different sidebars