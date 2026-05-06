Guide to the site structure and methods of updating.

# Team Members
About > Team Members
## Overview
Team member information is stored as one file per team member in the directory `_team`
This information is used to
- create the individual pages by using that information to automatically populate an HTML layout
- generate the link list on the main "Team Members" page

## Directories & Files 

`/about/team-members.md`
	The landing page for information on team members; contains any overall information as well as an automatically generated link list of the individual team members.

`/_layouts/team-member.html`
	An HTML layout used to automatically generate each individual team member page.

`/_team/`
	Directory containing markdown files with individual team member information as well as a template file. Collectively, these files (with the exception of the template file) populates the link list.
`/_team/first_initial-last_name.md`
	The only file needed to add and update information for an individual team member. This information is used to automatically populate both the link list and an individual member's page.

`/assets/images/team/`
	Directory in which photos of individual team members are stored in the convention `first_initial-last_name.md`

### Editing Team Members

#### Add a new team member
1. Make a new copy of the template ( `_template-team-member.md` found within the `/_team/` directory) and keep the copy in the same directory as the template
2. Rename the copy using the convention `first_initial-last_name.md`
3. Fill out the information for the team member. If a team member does not have a specific social media profile, such as LinkedIn, remove that line from the file.
	Example:
	```yml
	github: "https://github.com/jsmith"
	linkedin: "https://linkedin.com/in/jsmith"
	website: "https://jsmith.lab.edu"
	```
	becomes:
	```yml
	github: "https://github.com/jsmith"
	website: "https://jsmith.lab.edu"
	```
4. Make sure that the individual has a picture uploaded to the `/assets/images/team/` directory following the naming convention `first_initial-last_name.jpg` (or `.png` if your image is a PNG file)
AND the full file path is filled out in the [<abbr title ="located between the pair of `---`'s at the top of a markdown document">yml</abbr>](#yml) section
#### Editing an existing team member
1. Find the markdown document associated with that team member in the `/_team/` directory
2. Make your desired edits

> **Note:** Edits to an individual team member's markdown file that change the layout (for example, removing "Selected Publications") does not change that across all team member pages.
> At the moment, the content below the yml section is laid out in the order it appears in the markdown file (the individual headings are not organized by the HTML layout beyond placement relative to the [<abbr title ="located between the pair of `---`'s at the top of a markdown document">yml</abbr>](#yml) content)


# Helpful Terms
<a name="yml"></a>
<dl>
  <dt><strong>yml</strong></dt>
  <dd><em>Yet Another Markup Language (AKA Front Matter)</em><br/>Information stored as <code>key:value</code> pairs, generally located between the pair of <code>---</code>'s at the top of a markdown document OR within a <code>*.yml</code> file.</dd>
  <dd>Each <code>key: value</code> pair is a variable (<code>key</code>) and its value for that specific page (<code>value</code>). This allows the variable to be referenced and the value to be utilized as appropriate to the context.
  <br>For example, the HTML layout for the Team Members page uses `name: "Jane Smith"` to populate the name for an entry on link list as well as the name on Jane Smith's individual team member page.</dd>
</dl>