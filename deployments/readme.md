# LogicSpot Deployment Process

## Support Work Deployment

- Gather all tickets for a project that needs deploying.
- Review deployment notes for all tickets to find blockers / be aware of tasks.
- Get approval for the deployment.
- Create a release branch.
- Merge each feature branch into your release
    - You can ignore compiled conflicts such as .css where we'll be recompiling later.
    - Some conflicts may require pulling in another developer to resolve.
- Once all features are merged, ensure you've got all the npm packages, 
and bower components before compiling asssets.
    - Most projects are running gulp with the special command `gulp --production` which will minify, remove sourcemaps etc.
- Your release should be fully built at this point and ready to deploy, so bring up your local enviroment and test that the styles and working, there's no PHP errors or fatal errors on main pages.
- Merge your release branch to master
    - Don't forget to create a new commit even if fast forward is possible. This can be done using the `--no-ff` flag.
- Log into the admin areas of the sites and navigate to pages required for clearing Cache.
    - Don't forget some sites require a CDN invalidation.
    - Don't forget some sites are running Redis.
- Do any pre-deployment amendments noted in deployment notes.
- Deploy the code.
- Clear the Cache
- Do any post-deployment amendments noted in deployment notes.
- Test each feature you've deployed
- Test any main pages not covered by your feature testing.
- Test the primary user flow.
    - Homepage -> Category Page -> Product Page -> Adding to cart -> Viewing cart (if enabled) -> Going to checkout
- Send tickets to AM for a second round of testing and to inform the client.
