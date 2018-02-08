
# ICA_AROMA Nipype Workflow

This is just a basic Nipype workflow. 

The ICA-AROMA code itself comes from: https://github.com/maartenmennes/ICA-AROMA/
My only contribution was wrap this in Nipype workflow for easier integration into your existing pipelines, and also enable the user to specify any mapping between the subject functional and MNI space, so that you can use ICA-AROMA with ANTS-based registrations, for example.


Reference: 
* Raimon H.R. Pruim, Maarten Mennes, Daan van Rooij, Alberto Llera, Jan K. Buitelaar, Christian F. Beckmann, ICA-AROMA: A robust ICA-based strategy for removing motion artifacts from fMRI data, NeuroImage, Volume 112, 2015, Pages 267-277, ISSN 1053-8119, https://doi.org/10.1016/j.neuroimage.2015.02.064.



## Usage

```
aroma = create_ica_aroma_workflow(N_TRANSFORMS_FUNC2MNI)
aroma.base_dir = os.path.join(work_dir,'ica_aroma') #os.path.abspath('./work')
	
aroma.inputs.incoming.tr             = TR  # Set this to the proper TR
aroma.inputs.incoming.denoise_type   = 'nonaggr' # aggr/nonaggr
aroma.inputs.incoming.sample_func    = 'sample_func.nii.gz' # representative EPI image (used for mask generation)
aroma.inputs.incoming.in_file        = 'func.nii.gz' # input EPIs
aroma.inputs.incoming.par_file       = 'motion_parameters.txt' # tabular data file with 6 columns corresponding to the 6 DOFs of motion
aroma.inputs.incoming.func2mni_transf= [] # set of transformations that bring you from the subject functional space to MNI space.
aroma.inputs.incoming.melodic_dir    = 'melodic' # the directory where MELODIC output will go

```


