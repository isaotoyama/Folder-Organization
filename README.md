# Folder-Organization

Frontend Application Folder Structure

Root
docs—it’s an automatically generated folder with documentation for the code. We are using JSDoc to describe all our code, and we also run a job that builds navigable HTML documentation, which is easily available and deployed to our environments for quick reference.
reports—all reports from unit tests, end-to-end tests, visual tests, and performance tests land here. We deploy all HTML reports with our code to allow us to see all test results for the given version on each environment.
scripts — deployment scripts, pipeline files, etc., to support all build-related processes.
src — all of our source code, which we will focus on below in the rest of this post.
tests—all scripts, configs, helpers, utilities, and other things needed for all types of testing, all in one place.
public—which is, of course, our code after the build and ready for release.


Admin — is an application that helps us manage users, businesses, data, sales, and other typical administrative tasks to provide our services to customers.
Client — the frontend-facing applications used by our customers, which are the core of our business and the biggest one here.
DesignSystem — we have a separate application that displays all our design system components (a homemade Storybook, if you like). Its purpose is to share all reusable components with the business and other teams and remind them how everything looks “right now” in case they have any doubts. It helps frontend engineers who can access all component examples, get the implementation code (without opening the actual source code), and save time. We also use the DesignSystem app to run all our visual tests on each release to find UI changes and highlight errors.
Developers—this application serves as a Developer Platform for our customers. It is similar to the Client application but for a different audience.


assets—all extra things needed for the application. These might be logos and images that are used in multiple places. You might also find the “assets” folder in any component or view folder where things are more local.
components — reusable components across the whole application. Each subfolder is responsible for one component only and might have extra folders like tests, assets, and lang. Each components folder has an index.vue/jsx file as a “starting point” is (this is a very important bit, although it might feel weird, I know).
composables—reusable, state-aware logic for Vue/React. In our case, this folder doesn’t hold much (yet). Since the functionality differs from components or modules, we decided to keep these separate.
lang — translations folder where we keep all reusable text across the applications. Note that practically every component or view in the app has its own lang folder with more strings. This folder is quite specific to how we handle application translations and make text strings separate from the code itself. Ps. I wrote about our translation layer in one of my older posts, and if you are interested, go to my profile and find it :)
modules—JS-only code that can be reused anywhere in the given application (we have a modules folder in Core, too) and doesn’t require styles and HTML. These might be utilities, data transformation code, custom tracking implementation, etc.
static—static assets and pages that should be deployed with the application but are not used directly by the main code. Imagine things like a 404 page, no access page, or maybe a Not Supporter Browser error page (we’ve got one of these).
store — all Vue’s/React store files are in one place as none are closely bonded to a particular component or view (they should never be). The store is split into smaller files to isolate by purpose, such as user, business, products, reports, etc. All are easy to maintain and use across the whole application, built to be useful anywhere, not in a particular component.
tests—end-to-end tests are written in Playwright to cover the app’s top-level functionality. You can find /test folders all around the views and components as they cover particular areas and functionality.
views — all pages that can be viewed in the applications. Subfolders closely resemble what I have described so far, often having subfolders for assets, local components, and tests. Each folder contains router configuration for the given view; hence, we don’t have a top-level router folder serving any purpose. I explain this slightly more in the “quirks” section below.
