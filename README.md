package com.example.photo_editor;

import java.io.FileNotFoundException;
import java.io.IOException;

import android.net.Uri;
import android.os.Bundle;
import android.app.Activity;
import android.content.Intent;
import android.graphics.Bitmap;
import android.view.Menu;
import android.widget.ImageView;
import android.widget.Toast;

public class Activity_Result extends Activity {

	private static final int CAMERA_IMAGE_REQUEST = 0;

	protected void onActivityResult(int requestCode, int resultCode, Intent data) {
	    // TODO Auto-generated method stub
	    super.onActivityResult(requestCode, resultCode, data);

	    if (resultCode == RESULT_OK) {

	        switch (requestCode) {
	        case CAMERA_IMAGE_REQUEST:

	            Bitmap bitmap = null;
	            try {
	                GetImageThumbnail getImageThumbnail = new GetImageThumbnail();
	                Uri fileUri = null;
					bitmap = getImageThumbnail.getThumbnail(fileUri, this);
	            } catch (FileNotFoundException e1) {
	                // TODO Auto-generated catch block
	                e1.printStackTrace();
	            } catch (IOException e1) {
	                // TODO Auto-generated catch block
	                e1.printStackTrace();
	            }

	            // Setting image image icon on the imageview

	            ImageView imageView = (ImageView) this
	                    .findViewById(R.id.imageView1);

	            imageView.setImageBitmap(bitmap);

	            break;

	        default:
	            Toast.makeText(this, "Something went wrong...",
	                    Toast.LENGTH_SHORT).show();
	            break;
	        }

	    }
	}
}
