# Developer Notes

Internal notes and tips for maintaining this documentation.

## 🏗️ Architecture Decisions

### Navigation Structure

**Decision**: 2 main tabs instead of 4
- **CLI tab**: All developer content (34 pages)
- **Chat Widget tab**: All widget content (12 pages)

**Rationale:**
- Simpler navigation for users
- Clear separation of concerns (building vs embedding)
- Less cognitive load
- Easier to find content

### Content Organization

**Decision**: Group by user journey, not by content type

**CLI Tab Groups:**
1. Getting Started → Onboard new users
2. Core Concepts → Build understanding
3. CLI Commands → Reference material
4. API Reference → Technical details
5. Template & Examples → Learning resources

**Rationale:**
- Progressive learning path
- Users can follow natural progression
- Quick reference easily accessible
- Examples available when needed

## 🎨 Design Decisions

### Color Scheme

**Primary**: `#8B5CF6` (Purple)
**Light**: `#A78BFA`
**Dark**: `#7C3AED`

**Rationale:**
- Matches Lua AI brand
- Professional tech aesthetic
- Good contrast and readability
- Consistent with AI/tech industry standards

### Component Usage Patterns

**Cards** - For navigation and feature highlights
**Steps** - For sequential processes
**Tabs** - For alternative approaches
**Accordions** - For FAQs and collapsible content
**CodeGroup** - For language/framework alternatives

## 📊 Content Metrics

### Page Distribution

- **CLI**: 34 pages (74%)
- **Chat Widget**: 12 pages (26%)
- **Total**: 46 pages

### Content Types

- **Tutorials**: 8 pages (Getting started, first skill, etc.)
- **Concepts**: 4 pages (Architecture explanations)
- **Reference**: 14 pages (CLI commands, API methods)
- **Examples**: 12 pages (Working code examples)
- **Guides**: 8 pages (Configuration, styling, migration)

## 🔧 Maintenance Tasks

### Regular Updates Needed

**Monthly:**
- [ ] Check for outdated dependencies in examples
- [ ] Verify all external links still work
- [ ] Update screenshots if UI changed
- [ ] Review and update "coming soon" features

**Quarterly:**
- [ ] Review analytics for popular pages
- [ ] Identify gaps in documentation
- [ ] Collect user feedback
- [ ] Plan new content based on support tickets

**As Needed:**
- [ ] Update for new CLI versions
- [ ] Add new API methods
- [ ] Document new features
- [ ] Fix reported issues

### Link Maintenance

```bash
# Check for broken links regularly
mint broken-links

# Update links when:
# - Page moves or renames
# - External site changes URL
# - API endpoint changes
```

## 🎯 Quality Standards

### Code Examples Must:
- ✅ Be complete and runnable
- ✅ Include proper error handling
- ✅ Use TypeScript when applicable
- ✅ Show expected output
- ✅ Include all necessary imports
- ✅ Follow security best practices

### Pages Must Have:
- ✅ Clear frontmatter (title, description)
- ✅ Overview section
- ✅ Practical examples
- ✅ "Next Steps" with related pages
- ✅ Proper component usage
- ✅ No broken links

### Documentation Must:
- ✅ Be technically accurate
- ✅ Include security warnings where needed
- ✅ Show best practices
- ✅ Cover error cases
- ✅ Provide troubleshooting
- ✅ Link to related resources

## 🔍 Common Maintenance Tasks

### Adding a New API Method

1. **Update API reference page** (`api/[api-name].mdx`)
2. **Add code example** showing usage
3. **Update overview page** if significant
4. **Add to examples** if it's a common pattern
5. **Update changelog**

### Adding a New CLI Command

1. **Update CLI overview** (`cli/overview.mdx`)
2. **Create detailed page** if complex (or add to existing)
3. **Add to workflow examples**
4. **Update troubleshooting** with common issues
5. **Update changelog**

### Deprecating a Feature

1. **Add deprecation warning** to relevant pages
2. **Suggest alternative** approach
3. **Keep old docs** for historical reference
4. **Update migration guide** if needed
5. **Note in changelog**

## 📝 Writing Tips

### For Tutorials

- Start with the goal ("Build a task management skill")
- Break into clear steps
- Show complete code at each step
- Include testing instructions
- End with next steps

### For Reference Docs

- Start with overview and use cases
- List all options/methods clearly
- Use tables for parameter lists
- Include complete examples
- Show error handling

### For Examples

- Use real-world scenarios
- Include complete, runnable code
- Explain key concepts
- Show expected output
- Link to related reference docs

## 🚨 Common Pitfalls

### Avoid These

❌ **Incomplete code examples**
- Always show full imports and context

❌ **Outdated screenshots**
- Update when UI changes

❌ **Broken internal links**
- Test all links before committing

❌ **Missing frontmatter**
- Every page needs title and description

❌ **Inconsistent terminology**
- Use same terms throughout (skill vs capability)

❌ **Too much jargon**
- Explain technical terms

❌ **No error handling in examples**
- Always show proper error handling

## 🔄 Update Workflow

### When CLI Changes

1. Review release notes
2. Identify documentation impact
3. Update affected pages
4. Add new examples if needed
5. Test code examples
6. Update changelog
7. Deploy updated docs

### When API Changes

1. Update API reference pages
2. Update code examples
3. Update tutorials using that API
4. Add migration guide if breaking
5. Update changelog
6. Deploy

### When Widget Changes

1. Update configuration reference
2. Update code examples
3. Test in multiple frameworks
4. Update screenshots if UI changed
5. Update changelog
6. Deploy

## 📦 Release Process

### Documentation Releases

1. **Prepare changes** in feature branch
2. **Test thoroughly** locally
3. **Update changelog** with changes
4. **Create pull request** to main
5. **Review and approve**
6. **Merge to main** → auto-deploys
7. **Verify production** deployment
8. **Announce** in changelog/release notes

## 🎯 Future Improvements

### Short Term (1-3 months)
- Add interactive code playground
- Include more video tutorials
- Add community examples section
- Improve search functionality
- Add feedback widget on pages

### Long Term (6-12 months)
- Multi-language support
- API versioning docs
- Interactive examples with live output
- Community contribution portal
- Advanced use case studies

## 📞 Contact

### For Documentation Issues
- **Discord Community**: https://discord.gg/SRPEuwCzaD
- **Email**: docs@heylua.ai

### For Lua Platform Issues
- **Discord Community**: https://discord.gg/SRPEuwCzaD
- **Support**: support@heylua.ai
- **Sales**: sales@heylua.ai
- **General**: hello@heylua.ai

---

**Last Updated**: October 4, 2025
**Documentation Version**: 2.0.0
**Total Pages**: 46
**Maintainers**: Lua Documentation Team

