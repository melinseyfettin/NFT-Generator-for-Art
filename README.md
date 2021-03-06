# Akdeniz University 
# Engineering Faculty
# Department of Computer Engineering

# Senior  Project README File

- Students’ Name Surname : Melin Seyfettinoğlu
- Students’ ID Number : 20170808002
- Supervisor Name(s) : Murat Ak

# NFT Generator for Art

 Create generative art by using the canvas api and node js.
 
 As importance of NFTs grows many projects and programs are trying to create all kinds of art, music, videos and etc. Basicly everything can be a art peace or worth money.  There are many generators around, some of them code based some of them not. The project will be code generative and it will create arts by combining different layers

## Project Setup
- install `node.js` on your local system
- run `yarn install` to install dependencies

## Project Description

The Project will create arts by combining different layers of png files and generate one piece of art. It will accomplish that by using their given rarity values such as “super rare”, “rare”, “original” can be values for rarities. It will generate arts by requested rarity values and it will give us random matched arts in given rarity value. 

# How to Use
## Run The Code
1. Run `node index.js`
2. Open the `./output` folder to find your generated images to use as NFTs, as well as the metadata to use for NFT marketplaces.

## Adjust The Provided Configuration and Resources
### Configuration File
The file `./input/config.js` contains the following properties that can be adjusted to your preference in order to change the behavior of the NFT generation procedure:
- width: - of your image in pixels. Default: `1000px`
- height: - of your image in pixels. Default: `1000px`
- dir: - where image parts are stored. Default: `./input`
- description: - of your generated NFT. Default: `This is an NFT made by the generative code.`
- baseImageUri: - URL base to access your NFTs from. This will be used by platforms to find your image resource. This expects the image to be accessible by it's id like `${baseImageUri}/${id}`.
- startEditionFrom: - number (int) to start naming NFTs from. Default: `1`
- editionSize: - number (int) to end edition at. Default: `10`
- editionDnaPrefix: - value (number or string) that indicates which dna from an edition is used there. I.e. dna `0` from to independent batches in the same edition may differ, and can be differentiated using this. Default: `0`
- rarityWeights: - allows to provide rarity categories and how many of each type to include in an edition. Default: `1 super_rare, 4 rare, 5 original`
- layers: list of layers that should be used to render the image. 

### Image Layers 
The image layers are different parts that make up a full image by overlaying on top of each other. To ensure uniqueness, we want to add various features and multiple options for each of them in order to allow enough permutations for the amount of unique images we require.

To start, copy the layers/features and their images in a flat hierarchy at a directory of your choice (by default we expect them in `./input/`). The features should contain options for each rarity that is provided via the config file.

After adding the `layers`, adjust them accordingly in the `config.js` by providing the directory path, positioning and sizes.
Use the existing `addLayers` calls as guidance for how to add layers. This can either only use the name of the layer and will use default positioning (x=0, y=0) and sizes (width=configured width, height=configure height), or positioning and sizes can be provided for more flexibility.

### Allowing Different Raritie for Certain Rarity/Layer Combinations
It is possible to provide a percentage at which e.g. a rare item would contain a rare vs. common part in a given layer. This can be done via the `addRarityPercentForLayer` that can be found in the `config.js` as well. 
This allows for more fine grained control over how much randomness there should be during the generation process, and allows a combination of common and rare parts.

### Metadata Information
The program will output all the images in the `build/images` directory along with the metadata files in the `build/json` directory. Each collection will have a `_metadata.json` file that consists of all the metadata in the collection inside the `build/json` directory. The `build/json` folder also will contain all the single json files that represent each image file.
