Pipeline to deploy Bff

You can find example with values in notion!

1. Change vars.
   ToolsRoot - folder git init root folder
   Specify NugetFeed and TerraformRoot
2. In yaml file
   paths - include

3. task ArtifactoryDotnetCore@1
   Write correct rootPath! it is path to bff.sln file

4. task UseDotNet@2
   specify version. But maybe this task is not needed at all, unless
   new version of .Net appears, which is not bound to Azure Pipline yet.

5. task DotNetCoreCLI@2 build
   specify projects (path to bff.sln file) looks like $(ToolsRoot)/Bff.sln

6. task DotNetCoreCLI@2 publish
   specify projects (path to bff.sln file) looks like $(ToolsRoot)/Bff.sln

7. task PublishBuildArtifacts@1
   Pay attention to ArtifactName and PathtoPublish! Check values in Notion.

8. Line 169 download step.
   Check artifact name

9. task AzureWebApp@1 package. Check path with notion!

10. Line 287 Step download.
    Check artifact.

11. Line 289 task AzureWebApp@1
    Check package folder!

12. Check all the names like api-template, api, Template with notion exapmles. Might be some differences
