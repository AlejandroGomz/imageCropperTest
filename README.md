# imageCropperTest
CanHub Image Cropper Open Gallery


small test app on Java which allows to open Android gallery and returned selected image URI (using ActivityResultContracts.StartActivityForResult).

    private ActivityResultLauncher<Intent> openGalleryResultLauncher = registerForActivityResult(
            new ActivityResultContracts.StartActivityForResult(),
            new ActivityResultCallback<ActivityResult>() {
                @Override
                public void onActivityResult(ActivityResult result) {
                    if (result.getResultCode() == Activity.RESULT_OK) {
                        Log.d(TAG, "onActivityResult...handle open gallery");
                        Uri imageUri = result.getData().getData();
                        Log.d(TAG, "onActivityResult...handle open gallery for URI: "+imageUri);
                    } else {
                        Log.e(TAG, "onActivityResult...can't handle open gallery");
                    }

                }
            }
    );

    private void openGallery() {
        Intent gallery = new Intent(Intent.ACTION_PICK, MediaStore.Images.Media.INTERNAL_CONTENT_URI);
        //*startActivityForResult(gallery, PICK_IMAGE);
        openGalleryResultLauncher.launch(gallery);
    }
