## Questions
- where do we put `GlobalFiltersBar`?

## Possible refactoring
- AuthenticatedNavLink should become just `<ShowMeWhen />`
- shared `<Sidebar />` doesn't need to know about `userInfo` and `versionInfo`, these can be provided to children or filtered on in advance
- layouts can be used to show different sidebars as well

## How to
- ~~icons barrel file~~
- ~~visibleOnRoutes not needed anymore~~
- Sidebar will provide context open/closed
- companyRelativePrefix export not needed
- new EnvironmentInfo component
- new MenuItem component
	- label
	- icon